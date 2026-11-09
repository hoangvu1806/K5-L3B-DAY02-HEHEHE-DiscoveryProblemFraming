# CP5 & CP6 - Thiết kế Quy trình Trước/Sau và Khung Quản trị Agentic AI (Bounded Autonomy)

**Người phụ trách:** Bùi Đặng Nhật Nguyên (`2A202603937`)
**Vai trò trong nhóm:** Owner problem, Domain expert vận hành hạ tầng và log đa tầng, phụ trách chính Mục 4 (CP5) và Mục 6 (CP6) trong `report/team/group_report.md`.

---

## 1. Giải đáp 5 câu hỏi chuyên môn hạ tầng (Domain Confirmation cho CP4, CP5, CP6)

Phần này làm rõ các thông số thực tế để nhóm thống nhất khi viết `Problem Statement v0/v1`, `Eval` và `Quyết định`:

1. **Con số giả định v0 "90-120 phút/sự cố" và số liệu kiểm chứng CP4 "15-30 phút khoanh vùng" khác nhau như thế nào?**
   - Ở giả định ban đầu (`v0`), con số 90-120 phút là ước lượng gộp cả **độ trễ phát hiện ngoài giờ (`MTTD`: 30-60 phút)** lẫn **thời gian điều tra và cô lập thủ công (`MTTI + MTTM`: giả định 55-70 phút)**.
   - Sau khi kiểm chứng qua **5 buổi phỏng vấn ở CP4**, thời gian kỹ sư trực tiếp tra cứu log để khoanh vùng tầng gây lỗi trong giờ hành chính thực tế chỉ mất **15-30 phút** (gồm mở log cổng vào `3-5 phút`, lọc nhiễu `5-10 phút`, tra chéo các nguồn log tìm tầng lỗi `10-15 phút`), còn điểm nghẽn lớn nhất nằm ở **độ trễ phát hiện và phản ứng sự cố ngoài giờ/ban đêm** (2/5 người được hỏi thường bị gọi dậy giữa đêm cho cả sự cố thật lẫn cảnh báo giả).
2. **Khi nào một sự cố được coi là "đã cô lập" (Contained/Isolated)?**
   - Với sự cố từ truy cập bất thường / dò quét lỗ hổng / làm nghẽn cổng vào: Khi tác nhân gây lỗi đã bị áp giới hạn tốc độ (`Rate-limit`) hoặc khóa tạm thời (`Temporary IP Block` có thời hạn tự mở `TTL 15 phút`) tại tầng cổng đón lưu lượng (Nginx/WAF) và tỷ lệ lỗi `5xx`/`4xx` trên cổng vào hạ về mức bình thường sau 2 phút kiểm chứng (`Self-Check`).
   - Với sự cố nằm sâu ở tầng ứng dụng hoặc cơ sở dữ liệu dùng chung (vượt quá phạm vi tự chặn ở cổng mạng): Khi hệ thống đã gom xong bộ bằng chứng có dẫn nguồn dòng log xuyên tầng kèm đề xuất xử lý và đánh thức đúng kỹ sư phụ trách (`HITL`).
3. **Kỹ sư và Agent có quyền truy cập các nguồn log như thế nào?**
   - Về chiều đọc (`Investigation`): Agent được cấp tài khoản dịch vụ có quyền **chỉ đọc (`Read-only`)** đối với các nguồn log được phép truy vấn, hoàn toàn không có quyền sửa/xóa log hay đọc dữ liệu bí mật kinh doanh.
   - Về chiều thực thi (`Containment`): Agent **không được cấp quyền chạy lệnh shell tự do**, mà chỉ được gọi một danh mục hàm kịch bản chuẩn đã tham số hóa (`Parameterized Runbooks`) ở tầng cổng vào khi đạt ngưỡng điểm tự tin.
4. **Nếu chỉ chuẩn hóa Dashboard, Correlation ID và `Rule` (không dùng AI) thì giải quyết được tới đâu?**
   - Giải quyết tốt khâu **lọc nhiễu định kỳ đầu vào** (tách kết nối giữ phiên WebSocket, tính ngưỡng cửa sổ trượt theo thứ/giờ để giảm cảnh báo giả sáng thứ Hai).
   - Tuy nhiên **không giải quyết được 2 điểm nghẽn cốt lõi**:
     - Thứ nhất, các sự cố hạ tầng (lỗi mạng, DNS, dò quét bảo mật từ bên ngoài, treo kết nối proxy) thường đứt gãy trước khi sinh ra `Correlation ID` của tầng ứng dụng, hoặc trải rộng trên hàng chục nguồn log khác định dạng nên vẫn cần suy luận ngữ cảnh để chọn nhánh điều tra.
     - Thứ hai, vào ban đêm khi không có người nhìn Dashboard, nếu dùng `Rule` cứng để tự động chặn IP thì rất dễ khóa nhầm người dùng thật lúc lưu lượng tăng đột biến.
5. **Ai chịu trách nhiệm ở các ca dưới ngưỡng tự tin?**
   - Kỹ sư trực ca (`On-call Engineer`) là người duyệt cuối cùng thông qua cơ chế **Con người trong vòng lặp (`HITL`)** đối với mọi ca có `Confidence Score` dưới `85%` hoặc bất kỳ sự cố nào chạm tới dịch vụ cốt lõi dùng chung.

---

## 2. Công thức định lượng `Confidence Score` và 3 cột mốc phân quyền (`Bounded Autonomy`)

Để tránh rủi ro mô hình ngôn ngữ (`LLM`) tự chấm điểm tự tin cao ảo (Overconfident Hallucination), điểm `Confidence Score (0-100%)` được thiết kế là **điểm tổng hợp từ 3 nhóm tín hiệu kỹ thuật độc lập**:

- **Thành phần 1 - Độ lệch thống kê thực tế (40% trọng số):** Mức vượt ngưỡng của tỷ lệ lỗi (`5xx`/`4xx`) hoặc tần suất truy vấn từ 1 nguồn so với đường cơ sở (baseline) cùng khung giờ sau khi đã lọc bỏ kết nối giữ phiên.
- **Thành phần 2 - Độ khớp bằng chứng xuyên tầng với kịch bản chuẩn (40% trọng số):** Có trích dẫn được mã dòng log/timestamp khớp nhau giữa cổng vào (Nginx) với nguồn log liên quan (tường lửa, DNS, ứng dụng) và khớp với mẫu sự cố đã định nghĩa trong Runbook hay không.
- **Thành phần 3 - Kiểm tra an toàn và danh sách trắng (`Whitelist` - 20% trọng số + điều kiện chặn cứng):** Đối tượng bị tác động không nằm trong dải IP nội bộ/đối tác (`Whitelist`) và không phải dịch vụ cốt lõi dùng chung (nếu nằm trong `Whitelist` hoặc dịch vụ cốt lõi thì tự động ép quyền tự thực thi về `0%`, bắt buộc qua `HITL`).

**Ba cột mốc vận hành (`Confidence Thresholds`):**

| Cột mốc `Confidence Score` | Điều kiện áp dụng | Hành động của hệ thống | Cơ chế an toàn đi kèm |
|---|---|---|---|
| **Dưới 60%** | Dấu hiệu yếu, có thể là dao động lưu lượng bình thường | Tự động ghi nhận vào log theo dõi ngầm, không phát cảnh báo đánh thức ca trực | Tiếp tục theo dõi cửa sổ trượt 5 phút tiếp theo |
| **Từ 60% đến dưới 85%** *(hoặc chạm dịch vụ cốt lõi)* | Có bất thường thật nhưng bằng chứng liên tầng chưa khép kín, hoặc sự cố nằm ở tầng ứng dụng/database dùng chung | **Kích hoạt `HITL`:** Dừng tự thực thi; đóng gói bộ bằng chứng log đa nguồn kèm giải thích lý do điểm tự tin chưa đạt 85% và gợi ý lệnh xử lý để kỹ sư bấm duyệt | Kỹ sư trực ca chỉ mất 2-5 phút đọc bằng chứng có dẫn nguồn thay vì 60 phút tự mò từ đầu |
| **Từ 85% trở lên** *(và thuộc phạm vi cục bộ ở cổng vào)* | Bằng chứng rõ ràng (ví dụ 1 IP ngoại lai gửi hàng nghìn truy vấn dò quét lỗ hổng gây lỗi hàng loạt vào ban đêm) | **Agent tự chủ thực thi (`Auto-Containment`):** Gọi hàm `Parameterized Runbook` (như áp `rate-limit` hoặc khóa tạm IP trong 15 phút) | 1. Tự động hết hạn sau 15 phút (`Auto-TTL`).<br>2. Tự đọc lại log sau 2 phút (`Self-Check`); nếu lỗi không giảm thì tự gỡ lệnh chặn.<br>3. Gửi thông báo kèm nút **Hoàn tác 1 chạm (`1-click Rollback`)**. |

---

## 3. Liên kết sang Mục 4 và Mục 6 trong `report/team/group_report.md`

Toàn bộ sơ đồ `Mermaid` của Quy trình hiện tại (`4.1`), Quy trình tương lai (`4.2`), Bảng so sánh `Before/After` (`4.3`), Ma trận `mơ hồ x phức tạp` (`6.1`), Bảng so sánh 4 mức can thiệp (`6.2`), `AI Canvas` (`6.3`) và 2 câu hỏi `Google PAIR` (`6.4`) đã được điền trực tiếp vào `report/team/group_report.md`.

