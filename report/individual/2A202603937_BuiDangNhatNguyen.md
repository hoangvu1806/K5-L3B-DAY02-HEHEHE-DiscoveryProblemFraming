# Báo cáo cá nhân: 2A202603937_BuiDangNhatNguyen

> Đổi tên file theo quy tắc `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md` (MSSV trước, dấu `_`, họ tên viết liền không dấu). Sửa cả dòng tiêu đề phía trên cho khớp.
> Template chi tiết và prompt mẫu cho từng mục: [docs/01-worksheet.md](../../docs/01-worksheet.md).
> Mỗi thành viên một file trong `report/individual/` trên repo nhóm: copy template này thành file mới, điền, rồi commit bằng tài khoản GitHub của bạn. Không viết hộ người khác.

## 1. Thông tin học viên

- Họ tên: Bùi Đặng Nhật Nguyên
- MSSV: 2A202603937
- Email trường (không bắt buộc, repo có thể để public): không công khai
- Tên nhóm: HEHEHE
- Link repo nhóm: https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming

---

## 2. Scan problem (CP1)

Lăng kính: **Lặp lại**, **Tốn thời gian**, **Cần đọc, tổng hợp nhiều thông tin**, **Pain từ người khác**.

| # | Lăng kính | Job Story: Khi… tôi muốn… để… | Ai chịu ảnh hưởng? | Dấu hiệu thật (thời gian, tần suất, số người, bằng chứng) |
|---:|---|---|---|---|
| 1 | Tốn thời gian | Khi dịch vụ nội bộ báo lỗi hàng loạt, tôi muốn hệ thống vận hành có thể tự khoanh vùng ngay sự cố nằm ở tầng nào (cổng proxy, mạng, ứng dụng hay database) giữa hàng chục nguồn log mà không phải đăng nhập từng máy chủ đọc dò thủ công, để khôi phục dịch vụ trong vài phút | Kỹ sư vận hành, người dùng hệ thống | Hạ tầng thực tế có rất nhiều nguồn log rời rạc; mỗi lần sự cố xảy ra mất 60 đến 90 phút mở từng máy chủ và lọc log bằng tay |
| 2 | Cần đọc, tổng hợp nhiều thông tin | Khi xuất hiện dấu hiệu bất thường ở cổng đón lưu lượng (như Nginx), tôi muốn tự động lần tiếp sang đúng các file log ứng dụng, DNS hoặc xác thực có liên quan tùy theo từng loại lỗi, để tìm ra nguyên nhân gốc mà không bị chìm trong hàng triệu dòng log nhiễu | Kỹ sư vận hành, lập trình viên backend | Mỗi lần truy vết thủ công qua nhiều tầng log mất 45 đến 60 phút; các kỹ sư trong ca trực dễ kết luận lệch nhau do mỗi người chỉ kịp đọc vài file log |
| 3 | Cần đọc, tổng hợp nhiều thông tin | Khi có truy cập dò quét lỗ hổng hoặc gửi request dồn dập vào ban đêm lúc không có người trực màn hình, tôi muốn những trường hợp đã rõ bằng chứng được tự động cô lập ngay, còn ca phức tạp thì giữ lại chờ kỹ sư duyệt, để vừa chặn kịp thời vừa không chặn nhầm người dùng thật | Kỹ sư vận hành, quản trị viên bảo mật | Ca đêm thường mất 30 đến 60 phút mới có người nhận biết và phản ứng tay; ngược lại nếu đặt lệnh chặn cứng nhắc không xét ngữ cảnh thì dễ khóa nhầm kết nối hợp lệ |
| 4 | Pain từ người khác | Khi một dịch vụ phía sau quá tải kéo theo lỗi dây chuyền sang các dịch vụ khác, người dùng muốn sự cố được tự phát hiện và xử lý ngay từ lúc lỗi mới chớm tăng, để công việc không bị đình trệ và không phải gửi ticket báo lỗi | Người dùng hệ thống, đội trực hỗ trợ | Đội vận hành thường chỉ biết sự cố sau 30 đến 60 phút khi người dùng đã gửi nhiều tin nhắn hoặc ticket phàn nàn |
| 5 | Lặp lại | Khi kiểm tra sức khỏe cụm máy chủ hàng tuần, tôi muốn có sẵn bộ chỉ số chuẩn về lưu lượng và tỷ lệ lỗi trên từng dịch vụ, để biết ngay thành phần nào đang suy giảm mà không phải gõ lại lệnh thống kê trên từng máy chủ | Kỹ sư vận hành, quản lý hạ tầng | Đều đặn mỗi tuần mất 35 đến 45 phút chạy lại các lệnh cắt lọc trên nhiều cụm log để tổng hợp tình trạng hệ thống |
| 6 | Lặp lại | Khi trực ca vào sáng đầu tuần lúc lưu lượng toàn công ty tăng tự nhiên, tôi muốn phân biệt được mức tăng theo chu kỳ làm việc với sự cố thật, để cơ chế phản ứng tự động không bị kích hoạt nhầm và kỹ sư không tốn thời gian đóng cảnh báo giả | Kỹ sư trực ca (On-call) | Mỗi sáng thứ Hai nhận nhiều lượt cảnh báo vượt ngưỡng tĩnh từ các máy chủ, mất 30 đến 40 phút/ca để kiểm tra rồi đóng cảnh báo giả |
| 7 | Tốn thời gian | Khi cần điều tra lại sự cố quá khứ trên diện rộng, tôi muốn gom hàng trăm file log khác định dạng từ nhiều máy chủ về một cấu trúc chung trước khi log tạm bị xoay vòng xóa mất, để giữ nguyên dấu vết phục vụ đối chiếu | Kỹ sư vận hành, kỹ sư dữ liệu | Mỗi lần gom và đọc tuần tự hàng loạt file log lịch sử từ nhiều nơi mất 45 đến 60 phút; từng gặp trường hợp máy chủ khởi động lại làm mất log tạm |
| 8 | Pain từ người khác | Khi sự cố nằm sâu ở tầng ứng dụng vượt quá phạm vi tự khắc phục ở cổng mạng, đội phát triển backend muốn nhận ngay chuỗi bằng chứng liên tầng kèm mức độ khẩn cấp và hướng xử lý đề xuất, để bắt tay sửa ngay mà không phải tự đọc log hạ tầng | Lập trình viên backend, kỹ sư trực ca | Kỹ sư trực ca mất thêm 25 đến 30 phút mỗi sự cố để gom các đoạn log từ nhiều nguồn và viết giải thích bàn giao cho đội ứng dụng |

**Nếu có dùng AI để gợi ý thêm:** ý nào AI gợi ý mà bạn giữ lại, ý nào bỏ và vì sao.

- Cách thực hiện: Tôi tự liệt kê trước 5 vấn đề (#1 đến #5) từ trải nghiệm kiểm tra log hệ thống (từ tầng cổng Nginx đến các dịch vụ phía sau) và bài toán phản ứng chậm vào ban đêm. Sau đó nhờ AI gợi ý thêm góc nhìn theo 4 lăng kính.
- Ý giữ lại: Giữ #6 (nguy cơ cảnh báo giả sáng đầu tuần làm kích hoạt nhầm quy trình xử lý), #7 (tốn thời gian gom hàng trăm file log khác định dạng) và #8 (điểm nghẽn bàn giao bằng chứng đa nguồn khi cần con người can thiệp sâu), viết lại theo thời gian thực tế đã gặp.
- Ý loại bỏ: Bỏ cách viết nhét thẳng chữ "cần xây dựng AI Agent" vào cột Job Story (vì quy định CP1 cấm đặt tên công cụ giải pháp vào câu mô tả vấn đề), và bỏ ý tưởng để hệ thống tự ý sửa mã nguồn hoặc tự khởi động lại toàn bộ cụm máy chủ không có ngưỡng kiểm soát.

---

## 3. Top 3 Problem Cards + quy trình nháp (CP2)

### Bảng chọn top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---:|---|---|---|
| 1 | Phát hiện chậm, phải lần mò thủ công qua hàng chục nguồn log rời rạc và không thể tự cô lập sự cố kịp thời vào ban đêm (#1, #2, #3, #4) | Mất nhiều thời gian nhất (60 đến 90 phút/sự cố); đặt ra trực diện bài toán thiết kế **AI tự chủ (Agentic AI)** biết tự chọn nguồn log điều tra và tự quyết định thực thi chặn lỗ hổng/sự cố dựa trên **ngưỡng điểm tự tin (`Confidence Score`) kết hợp con người trong vòng lặp (`HITL`)** | Cách tính `Confidence Score` như thế nào để phản ánh đúng độ chắc chắn thực tế (không bị ảo giác), và đặt cột mốc bao nhiêu phần trăm làm ranh giới giữa "Agent tự thực thi" với "Chờ con người duyệt"? |
| 2 | Cảnh báo giả vào giờ cao điểm đầu tuần dễ làm kích hoạt nhầm cơ chế phản ứng và gây quá tải cho ca trực (#6) | Lặp lại hàng tuần trên nhiều dịch vụ; là chốt chặn đầu vào bắt buộc phải giải quyết để hệ thống tự chủ phía sau không hành động sai trên nhiễu | Dùng công thức thống kê cửa sổ trượt (`Rule`) làm màng lọc đầu tiên đã chặn được hơn 80% nhiễu trước khi gọi tới Agent chưa? |
| 3 | Chậm trễ khi gom bằng chứng xuyên qua nhiều tầng log để bàn giao cho con người xử lý các ca dưới ngưỡng tự tin (#8) | Mắt xích quyết định hiệu quả của nhánh `HITL`: khi điểm tự tin dưới ngưỡng hoặc sự cố quá rủi ro để máy tự chạy lệnh, con người cần có sẵn hồ sơ bằng chứng đầy đủ để quyết định nhanh | Kỹ sư trực ca và đội backend cần những thông tin gì trên màn hình phê duyệt để có thể bấm duyệt hoặc bác bỏ lệnh đề xuất trong dưới 2 phút? |

### Problem Card #1

| Trường | Nội dung |
|---|---|
| Job Story | Khi hệ thống gặp lỗi hàng loạt hoặc bị khai thác bất thường (nhất là ngoài giờ hành chính), tôi muốn phát hiện sớm từ cổng vào, tự động lần ra đúng nguyên nhân gốc giữa hàng chục nguồn log liên quan và phân quyền xử lý theo độ tin cậy rõ ràng, để những mối đe dọa rõ ràng được cô lập tức thì trong vài phút còn ca nhạy cảm vẫn có con người kiểm soát |
| Actor | Kỹ sư trực vận hành hệ thống (IT / NetOps On-call) quản lý hạ tầng nhiều máy chủ và dịch vụ nội bộ |
| Thời điểm / bối cảnh | Khi lưu lượng hoặc tỷ lệ lỗi tăng đột biến (triệu chứng xuất hiện đầu tiên ở log cổng vào như Nginx, nhưng nguyên nhân gốc có thể nằm ở tấn công mạng, DNS, ứng dụng hoặc database), đặc biệt căng thẳng vào ban đêm khi không có người canh màn hình |
| Quy trình hiện tại (3–7 bước) | 1. Nhận báo lỗi trễ từ người dùng.<br>2. Mở log cổng vào (như Nginx access/error log) xem triệu chứng.<br>3. Gõ lệnh lọc bỏ bản ghi nhiễu (kết nối giữ phiên, cache) tìm khung giờ đỉnh lỗi.<br>4. Tùy dấu hiệu vừa đọc mà đăng nhập tiếp sang các máy chủ khác để tra log tường lửa, DNS, ứng dụng hoặc database.<br>5. Tự đánh giá mức độ chắc chắn rồi chạy lệnh xử lý (chặn IP hoặc báo đội ứng dụng).<br>6. Theo dõi lại log xem lỗi đã hết chưa và viết báo cáo. |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 3, Bước 4 và Bước 5: Mọi thao tác từ lọc nhiễu, quyết định mở tiếp nguồn log nào trong hàng chục nguồn log công ty cho đến gõ lệnh ngăn chặn đều phụ thuộc 100% vào con người thủ công, mất 60 đến 70 phút xử lý (cộng thêm 30 đến 60 phút phát hiện trễ ban đầu) |
| Impact (nếu không giải thì sao) | Tổng thời gian gián đoạn kéo dài 90 đến 120 phút (hoặc tới sáng hôm sau nếu xảy ra ban đêm), làm ngưng trệ dây chuyền nhiều dịch vụ hoặc để kẻ tấn công kịp dò quét sâu vào hệ thống |
| Success metric (baseline → target) | Giảm thời gian từ lúc phát sinh bất thường đến lúc cô lập xong từ 90-120 phút xuống dưới 5 phút đối với các ca đủ độ tin cậy tự động (và dưới 15 phút với ca chờ người duyệt); tỷ lệ cảnh báo sai dưới 15%; 0 trường hợp tự động chặn nhầm dải IP hoặc dịch vụ hợp lệ |
| Phương án không dùng AI | Gom log tập trung (OpenSearch/Loki) kèm quy tắc ngưỡng tĩnh (`Rule`) và script chặn cố định: nếu chỉ báo động thì ban đêm vẫn không có người xử lý kịp, còn nếu cho script tự chặn theo ngưỡng cứng nhắc thì rất dễ khóa nhầm người dùng thật lúc cao điểm |
| Giả thuyết về AI (nếu có) | Thiết kế **Agentic AI có tính tự chủ có kiểm soát (Bounded Autonomy)** vận hành qua 4 bước:<br>1. **Tự chủ điều tra đa nguồn:** Từ cảnh báo ở cổng vào (như Nginx), Agent tự suy luận và tự chọn công cụ mở tiếp các nguồn log liên quan (tường lửa, xác thực, ứng dụng, database) thay vì đi theo kịch bản cứng.<br>2. **Định lượng điểm tự tin (`Confidence Score` 0-100%):** Tính điểm tổng hợp từ mức vượt ngưỡng thống kê, độ khớp bằng chứng xuyên tầng với kịch bản chuẩn và kiểm tra danh sách trắng (không để LLM tự đoán cảm tính).<br>3. **Phân quyền thực thi theo cột mốc (`Confidence Thresholds` + `HITL`):**<br>  + Dưới mốc thấp (ví dụ < 60%): Tự động ghi nhận theo dõi, không báo động giả.<br>  + Giữa hai mốc (ví dụ 60% đến < 85%) hoặc đụng tới dịch vụ cốt lõi dùng chung: Dừng lại chuyển sang **Con người trong vòng lặp (`HITL`)**, gửi kèm bằng chứng log và câu lệnh đề xuất chờ kỹ sư bấm duyệt.<br>  + Vượt mốc cao (ví dụ >= 85%) và nằm trong danh mục hành động cục bộ an toàn: **Agent tự chủ thực thi ngăn chặn ngay** (như áp giới hạn tốc độ hoặc khóa tạm thời 1 IP đang khai thác lỗ hổng trong 15 phút).<br>4. **Tự kiểm chứng & Hoàn tác (`Self-Check & Rollback`):** Sau khi thực thi, Agent đọc tiếp log 2 phút sau để kiểm tra lỗi đã giảm chưa và gửi thông báo kèm nút Hoàn tác 1 chạm cho kỹ sư. *(Khi thử nghiệm thực tế sẽ áp dụng trước trên tầng cổng Nginx rồi mở rộng sang các nguồn log khác).* |
| Cảm nhận nhanh | Agent (bắt buộc cần tính tự chủ chọn nhánh nguồn log điều tra và tự chủ cô lập sự cố ban đêm, được kiểm soát chặt bằng cột mốc `Confidence Score` và `HITL`) |

Quy trình nháp hiện tại:

```text
HIỆN TẠI (khoảng 90 phút xử lý chủ động + 30-60 phút phát hiện trễ, 100% thủ công)

[1. Nhận báo lỗi trễ: 30-60p] -> [2. Mở log cổng vào (Nginx) xem triệu chứng: 10p]
-> [3. Lọc bỏ log nhiễu & tìm khung giờ đỉnh lỗi: 20p] (BOTTLENECK)
-> [4. Tự mò mở tiếp log ứng dụng / mạng / bảo mật trên server khác: 35p] (BOTTLENECK)
-> [5. Cân nhắc & gõ lệnh chặn IP / xử lý tay: 10p] (BOTTLENECK BAN ĐÊM)
-> [6. Kiểm tra lại & viết báo cáo: 15p]
```

### Problem Card #2

| Trường | Nội dung |
|---|---|
| Job Story | Khi trực ca vào giờ cao điểm đầu tuần, tôi muốn phân biệt chính xác mức tăng lưu lượng tự nhiên trên các máy chủ với đợt bất thường thật sự, để không kích hoạt nhầm quy trình phản ứng và không tốn thời gian kiểm tra cảnh báo giả |
| Actor | Kỹ sư trực ca vận hành (On-call Engineer) |
| Thời điểm / bối cảnh | Buổi sáng đầu tuần (8h30 đến 10h30 thứ Hai) khi toàn bộ nhân viên mở các công cụ làm việc khiến lượng kết nối trên nhiều dịch vụ tăng vọt so với cuối tuần |
| Quy trình hiện tại (3–7 bước) | 1. Nhận hàng loạt cảnh báo lưu lượng vượt ngưỡng cố định.<br>2. Mở log 30 phút gần nhất của các dịch vụ đang báo động.<br>3. Tách riêng các kết nối giữ phiên (WebSocket) và đếm tỷ lệ lỗi thật.<br>4. Mở số liệu sáng thứ Hai tuần trước để so sánh bằng mắt.<br>5. Xác nhận là bình thường và đóng từng cảnh báo. |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 3 và Bước 4: Tách lọc lưu lượng nhiễu và đối chiếu thủ công với cùng khung giờ tuần trước trên nhiều dịch vụ, mất khoảng 25 phút mỗi đợt kiểm tra |
| Impact (nếu không giải thì sao) | Tốn 30 đến 45 phút mỗi ca sáng đầu tuần; nếu nối thẳng cảnh báo nhiễu này vào một hệ thống tự động chặn thì rất dễ gây ra hành động chặn nhầm hàng loạt |
| Success metric (baseline → target) | Giảm tỷ lệ cảnh báo sai xuống dưới 15%; giảm thời gian xác minh cảnh báo đầu tuần từ 35-40 phút/ca xuống dưới 5 phút/ca |
| Phương án không dùng AI | Dùng `Rule` tách bỏ kết nối giữ phiên trước khi đếm, tính ngưỡng chuẩn riêng theo từng thứ trong tuần (cửa sổ trượt) và tắt lặp lại cảnh báo trong 30 phút |
| Giả thuyết về AI (nếu có) | Kết hợp màng lọc thống kê chu kỳ (`Rule`) với mô hình phát hiện bất thường đa chiều để chấm điểm sơ bộ chính xác trước khi đánh thức Agent vào cuộc điều tra sâu (giúp tiết kiệm chi phí token và ngăn Agent hành động trên nhiễu) |
| Cảm nhận nhanh | Rule kết hợp Workflow (đóng vai trò màng lọc đầu vào an toàn trước khi chuyển lên tầng Agent) |

Quy trình nháp hiện tại:

```text
HIỆN TẠI (khoảng 40 phút/ca kiểm tra cảnh báo đầu tuần)

[1. Nhận loạt cảnh báo ngưỡng tĩnh: 3p] -> [2. Mở log các dịch vụ báo động: 7p]
-> [3. Tách lọc log giữ phiên & đếm lỗi thật: 10p] (BOTTLENECK)
-> [4. So sánh tay với sáng thứ Hai tuần trước: 15p] (BOTTLENECK)
-> [5. Đóng các cảnh báo giả: 5p]
```

### Problem Card #3

| Trường | Nội dung |
|---|---|
| Job Story | Khi gặp sự cố liên tầng phức tạp nằm dưới ngưỡng được phép tự động can thiệp, tôi muốn có sẵn bản tổng hợp bằng chứng xuyên qua các nguồn log kèm câu lệnh khắc phục đề xuất, để kỹ sư trực ca và đội backend phê duyệt xử lý trong vài phút thay vì tự tra cứu lại từ đầu |
| Actor | Kỹ sư vận hành trực ca (người phê duyệt `HITL`) và Lập trình viên các đội backend (người phối hợp xử lý) |
| Thời điểm / bối cảnh | Khi sự cố chạm tới dịch vụ cốt lõi dùng chung hoặc nguyên nhân chưa đủ ngưỡng điểm tự tin để máy tự thực thi, bắt buộc chuyển giao cho con người ra quyết định |
| Quy trình hiện tại (3–7 bước) | 1. Cắt các dòng lỗi tiêu biểu lúc đỉnh lỗi ở cổng proxy.<br>2. Tra cứu tiếp sang log của các dịch vụ ứng dụng liên quan để tìm đúng dịch vụ gốc gây treo.<br>3. Tự ước lượng mức độ rủi ro.<br>4. Viết tin nhắn tóm tắt diễn biến, bằng chứng log và phương án đề xuất.<br>5. Gửi cho người có thẩm quyền / đội ứng dụng duyệt và trả lời câu hỏi làm rõ. |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 2 và Bước 4: Gom bằng chứng xuyên qua nhiều nguồn log và biên soạn phương án đề xuất để người duyệt đủ thông tin ra quyết định, mất khoảng 22 phút/sự cố |
| Impact (nếu không giải thì sao) | Làm chậm mắt xích con người phê duyệt (`HITL`) thêm 25 đến 30 phút; nếu thiếu bằng chứng rõ ràng thì người duyệt không dám bấm thực thi hoặc gửi nhầm nhóm phát triển |
| Success metric (baseline → target) | Giảm thời gian chuẩn bị hồ sơ phê duyệt và bàn giao sự cố từ 25-30 phút xuống dưới 3 phút/lần; 100% thông số khung giờ, tên dịch vụ và đường dẫn lỗi khớp với log gốc |
| Phương án không dùng AI | Biểu mẫu sự cố cố định kèm script tự gom khung giờ, mã lỗi và đường dẫn lỗi theo mã định danh truy vết (request ID) |
| Giả thuyết về AI (nếu có) | Khi `Confidence Score` nằm dưới ngưỡng tự thực thi (ví dụ dưới 85%), Agent tự động đóng gói các bằng chứng log đã thu thập ở nhiều tầng, giải thích lý do vì sao điểm tự tin chưa đạt mức tự chạy và đính kèm phương án xử lý gợi ý để con người chỉ cần kiểm tra và bấm xác nhận (`HITL`) |
| Cảm nhận nhanh | Workflow / nhánh HITL của Agent (hỗ trợ tăng tốc quyết định cho con người ở những ca không được phép tự động hoàn toàn) |

Quy trình nháp hiện tại:

```text
HIỆN TẠI (khoảng 35 phút gom bằng chứng xin duyệt & bàn giao xử lý)

[1. Cắt dòng lỗi ở cổng proxy: 5p] -> [2. Tra chéo sang log các dịch vụ ứng dụng: 10p] (BOTTLENECK)
-> [3. Đánh giá mức rủi ro: 3p] -> [4. Viết tóm tắt bằng chứng & đề xuất hướng sửa: 12p] (BOTTLENECK)
-> [5. Chờ hỏi đáp làm rõ & phê duyệt: 5p]
```

### Card muốn pitch nhất

- Card số: Card #1 (Phát hiện chậm, phải lần mò thủ công qua hàng chục nguồn log rời rạc và không thể tự cô lập sự cố kịp thời vào ban đêm).
- Vì sao: Thể hiện trọn vẹn lý do thực tế cần tới **AI tự chủ (Agentic AI)** trong vận hành hạ tầng đa nguồn log, đồng thời giải quyết bài toán cân bằng giữa tốc độ phản ứng tự động và độ an toàn thông qua cơ chế **cột mốc điểm tự tin (`Confidence Score`) kết hợp con người trong vòng lặp (`HITL`)**.
- Câu hỏi muốn nhóm phản biện: Khi thiết kế cột mốc `Confidence Score` (ví dụ mốc 85%) để phân chia giữa việc cho phép Agent tự thực thi chặn lỗ hổng/IP với việc bắt buộc chờ con người duyệt (`HITL`), chúng ta nên tính con số `Confidence Score` đó từ những tín hiệu kỹ thuật nào để tránh việc mô hình ngôn ngữ tự chấm điểm cao ảo rồi chặn nhầm cổng kết nối hợp lệ?

### AI đã phản biện card thế nào

| Điểm yếu AI chỉ ra | Đồng ý? | Đã sửa gì |
|---|---|---|
| Nếu mô tả như chỉ có 2 file log cố định thì `Workflow` tĩnh là đủ, không cần tới tính tự chủ của `Agent`; nhưng nếu cho `Agent` tự chủ gõ lệnh tự do trên toàn bộ hàng trăm máy chủ công ty ngay lập tức thì rủi ro làm sập hệ thống quá cao | Đồng ý | Làm rõ thực tế doanh nghiệp có hàng chục nguồn log đa tầng nên bắt buộc cần tính tự chủ của `Agent` để tự chọn nguồn log điều tra tiếp theo; đồng thời giới hạn quyền tự thực thi chỉ trong danh sách kịch bản chuẩn viết sẵn (Parameterized Runbook, không sinh lệnh shell tự do) và chạy Pilot thu hẹp ở tầng cổng Nginx trước |
| Nguy cơ điểm tự tin ảo: nếu hỏi trực tiếp LLM "bạn tự tin bao nhiêu phần trăm?" để xét cột mốc cho phép tự chặn, LLM rất hay trả về trên 90% ngay cả khi suy đoán sai nguyên nhân gốc | Đồng ý | Tách công thức `Confidence Score` thành điểm tổng hợp định lượng từ tín hiệu thống kê, độ khớp bằng chứng liên tầng và kiểm tra danh sách trắng (Whitelist); thêm bước Agent tự đọc lại log kiểm tra sau khi chặn kèm nút Hoàn tác 1 chạm cho kỹ sư |
| Ở các ca dưới ngưỡng `Confidence Score`, nếu chỉ dừng lại báo lỗi chung chung thì con người vẫn mất 30 phút tự đọc lại log từ đầu, làm mất ý nghĩa của hệ thống | Đồng ý | Thiết kế rõ nhánh `HITL` (liên kết sang Card #3): khi điểm tự tin dưới ngưỡng cho phép tự chạy, Agent vẫn phải bàn giao trọn bộ bằng chứng đã gom được cùng lý do dừng lại để kỹ sư duyệt nhanh trong vài phút |

---

## 4. Tôi đã tham gia phần nào (CP3 -> CP7)

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng tới bài nhóm |
|---|---|---|
| Pitch Problem Card | Trình bày Problem Card #1: bài toán kỹ sư trực vận hành mất 90-120 phút dò thủ công qua hàng chục nguồn log rời rạc và đề xuất kiến trúc Agentic AI tự chủ theo ngưỡng `Confidence Score` kết hợp `HITL` | Nhóm thống nhất chọn bài toán của tôi làm Candidate Problem chính thức của cả nhóm |
| Phản biện bài của bạn khác | Câu hỏi tôi đã đặt: Với card duyệt câu trắc nghiệm của Vũ: "Nếu dùng LLM tự giải lại để bắt lỗi đáp án trên các môn tự nhiên khó thì làm sao biết khi nào chính LLM giải sai?". Với card Text-to-SQL của Bảo: "Việc ánh xạ schema khi JOIN nhiều bảng là bài toán kỹ thuật bên trong giải pháp hay là vấn đề gốc của người dùng cuối?". Với card chấm code Python của Hà Anh: "Dùng Unit Test và Linter đã bắt được phần lớn lỗi cú pháp và kết quả chạy code chưa, và việc viết nhận xét cuối khóa 12 tuần mới làm 1 lần thì có đủ cấp thiết không?" | Giúp nhóm tách bạch bài toán giải được bằng `Rule` (Linter, Unit Test, BI Dashboard) với bài toán thực sự cần rẽ nhánh điều tra động bằng `Agent` |
| Nhận phản biện | Câu hỏi tôi nhận được: Con số 90-120 phút là thời gian điều tra hay khắc phục hoàn toàn? Khi nào một sự cố được coi là đã cô lập, và làm sao đảm bảo Agent không tự ý chạy lệnh làm sập môi trường thật? | Tôi đã sửa gì: Tách rõ thời gian khoanh vùng tầng lỗi trực tiếp (15-30 phút theo kết quả phỏng vấn CP4) khỏi tổng thời gian phát hiện và phản ứng trễ vào ban đêm; định nghĩa rõ quyền chỉ đọc (`Read-only`) khi tra log và khóa hành động ngăn chặn trong `Parameterized Runbook` có kiểm tra `Whitelist`, thời hạn tự mở 15 phút (`TTL`) kèm nút `1-click Rollback` |
| Gom cluster / cây OST | Phụ trách chính gom 12 card của 4 thành viên thành 3 Cluster (AIOps, EdTech, Text-to-SQL) và vẽ cây OST ở mục 2.2-2.3 | Tách rõ 3 nhánh Opportunity (nhiễu cảnh báo đầu vào, mất thời gian tra chéo log đa tầng, phản ứng trễ vào ban đêm) và gạch bỏ các ý tưởng solution đội lốt problem |
| Chọn candidate problem | Cùng nhóm lập bảng chấm điểm shortlist 7 tiêu chí và giải thích lý do chọn/loại ở mục 2.4 | Bài toán giám sát log đa nguồn đạt 33/35 điểm vì thể hiện rõ nhất sự khác biệt giữa 4 mức `No AI / Rule / Workflow / Agent` |
| Kiểm chứng / research | Đóng góp câu hỏi chuyên môn hạ tầng cho Vũ đi phỏng vấn 5 người làm DevOps/SRE/Backend và phối hợp cùng Hà Anh hoàn thiện bảng Research 3 công cụ (Datadog Watchdog, Dynatrace Davis AI, PagerDuty AIOps) | Kết quả phỏng vấn giúp nhóm điều chỉnh baseline khoanh vùng về 15-30 phút, chuyển trọng tâm sang phản ứng sự cố ngoài giờ và chốt 3 điều kiện bắt buộc khi tự chặn (`Whitelist`, `TTL 15 phút`, `Rollback`) |
| Quy trình nhóm | Phụ trách chính Mục 4 (`group_report.md`): vẽ 2 sơ đồ `Mermaid` (quy trình hiện tại 6 bước thủ công và quy trình tương lai kết hợp `Rule` + `Agent` + `Confidence Score` + `HITL` + `Rollback`) và lập bảng `Before/After`, sau đó hiệu chỉnh lại số phút ở mục 1, 2.3, 4.1, 4.3, 6.3 khớp với kết quả phỏng vấn CP4 | Chỉ rõ điểm nghẽn phản ứng ngoài giờ/ban đêm và bước tra chéo đa nguồn log (15-30 phút), đặt cơ sở luồng vận hành cho toàn bộ báo cáo nhóm |
| Problem Statement | Giải đáp 5 câu hỏi chuyên môn hạ tầng (trong `report/assets/2A202603937_cp5_cp6_workflow_and_ai_level.md`) để Bảo viết `Problem Statement v0/v1` | Thống nhất ranh giới cứng (`Boundary`): cấm sinh lệnh shell tự do, kiểm tra `Whitelist` và bắt buộc qua `HITL` với mọi dịch vụ cốt lõi dùng chung |
| Mức can thiệp AI | Phụ trách chính Mục 6 (`group_report.md`): lập ma trận `mơ hồ x phức tạp`, bảng so sánh 4 mức AI, `AI Canvas` và trả lời 2 câu hỏi `Google PAIR` | Chứng minh thuyết phục vì sao `Workflow` tĩnh không đủ khi đường điều tra rẽ nhánh qua hàng chục nguồn log phân tán và vì sao cần kiến trúc `Bounded Autonomy` |
| Quyết định | Cùng Hà Anh và cả nhóm thống nhất quyết định **Go - pilot có điều kiện** theo 2 giai đoạn tại tầng cổng Nginx kèm ngưỡng dừng (`Kill Criteria`) | Chạy Giai đoạn 1 (`Shadow/read-only`) trong 2 tuần trên tối thiểu 30 sự cố để hiệu chuẩn `Confidence Score` trước khi mở quyền tự cô lập cục bộ ở Giai đoạn 2 |

---

## 5. Dùng AI

| Checkpoint | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai hoặc hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| CP1 Scan | Rà soát cách viết Job Story theo 4 lăng kính cho bài toán vận hành đa nguồn log mà không vi phạm lỗi nhét từ khóa công nghệ vào cột vấn đề | Nhắc quy tắc không đưa chữ "AI" hay "Agent" vào cột Job Story của CP1 để tránh bị trừ điểm, và gợi ý thêm góc nhìn cảnh báo giả đầu tuần | Bản nháp đầu của AI hiểu hẹp rằng hệ thống chỉ có 2 file log cố định, diễn đạt còn mờ nhu cầu cần cơ chế tự khoanh vùng và tự cô lập sự cố vào ca đêm | Chỉnh lại đúng thực tế doanh nghiệp có hàng chục nguồn log đa tầng (Nginx chỉ là cổng vào), làm rõ nỗi đau khi thiếu phản ứng tự động an toàn lúc vắng người trực và xóa sạch mọi thông số riêng của công ty |
| CP2 Problem Card | Đóng vai Product Manager hoài nghi để phản biện thiết kế AI tự chủ (`Agentic AI`) dùng cột mốc `Confidence Score` kết hợp `HITL` | Chỉ ra 2 lỗ hổng quan trọng: rủi ro mô hình tự chấm `Confidence Score` ảo và rủi ro nếu cho Agent tự sinh lệnh hệ thống tùy ý thay vì khóa trong kịch bản cố định | Ban đầu AI rút gọn phần giả thuyết quá mức khiến cơ chế tự chủ 4 bước (tự chọn nguồn log, tính `Confidence Score`, phân mốc tự thực thi hay chuyển `HITL`, tự kiểm tra hoàn tác) chưa được thể hiện sâu | Viết chi tiết cơ chế tự chủ có kiểm soát vào Card #1, liên kết chặt 3 Problem Cards thành 3 mắt xích (Màng lọc nhiễu đầu vào -> Agent tự chủ theo `Confidence Score` -> Nhánh bàn giao bằng chứng cho `HITL` khi dưới ngưỡng) |
| CP4 Research | Tra cứu tài liệu kỹ thuật chính thức của các công cụ giám sát log (GoAccess, OpenSearch Anomaly Detection, Grafana Loki, Datadog Watchdog) để hỗ trợ nhóm đối chiếu | Tóm tắt nhanh cơ chế thuật toán (như Random Cut Forest của OpenSearch) và cung cấp đường dẫn tài liệu chính thức mở được | AI có xu hướng khen công cụ thương mại giải quyết được mọi thứ mà ít nhấn mạnh rào cản không được đẩy log nội bộ nhạy cảm lên đám mây bên thứ ba | Bổ sung rõ khoảng trống thực tế: công cụ mã nguồn mở miễn phí thì thiếu suy luận ngữ cảnh liên tầng, còn công cụ thương mại thì chi phí cao và vướng quy định bảo mật dữ liệu log nội bộ |
| CP5 Quy trình | Kiểm tra cú pháp sơ đồ `Mermaid` cho quy trình hiện tại (6 bước) và quy trình tương lai có phân nhánh theo ngưỡng `Confidence Score` | Giúp cấu trúc hóa sơ đồ luồng xử lý rõ ràng, tách biệt trực quan các bước `Rule`, `Agent`, `HITL` và nhánh `Fallback/Rollback` | Gợi ý ban đầu của AI gộp chung độ trễ phát hiện với thời gian kỹ sư thao tác thành một con số mơ hồ và thiếu cơ chế tự hết hạn lệnh chặn | Tách bạch rõ 30-60 phút phát hiện trễ với 60-70 phút thao tác điều tra; bổ sung cơ chế tự hết hạn sau 15 phút (`Auto-TTL`), bước Agent tự đọc lại log sau 2 phút (`Self-Check`) và nút `1-click Rollback` |
| CP5-6 Problem Statement | Phản biện chéo các tiêu chí định nghĩa "đã cô lập sự cố" và ranh giới an toàn (`Boundary`) để phối hợp với bạn viết Problem Statement | Nhắc các trường hợp biên như nguy cơ tấn công Prompt Injection qua chuỗi `User-Agent` trong log làm mô hình hiểu sai lệnh | Đề xuất của AI về công thức `Confidence Score` ban đầu còn định tính, chưa có điều kiện chặn cứng cho các dịch vụ quan trọng | Đặt quy tắc ép quyền tự thực thi về `0%` (bắt buộc qua `HITL`) nếu đối tượng nằm trong `Whitelist` hoặc chạm tới cơ sở dữ liệu/dịch vụ cốt lõi dùng chung |
| CP6 Mức can thiệp / quyết định | Phản biện lập luận so sánh 4 mức (`No AI / Rule / Workflow / Agent`), bảng `AI Canvas` và 2 câu hỏi `Google PAIR` | Giúp hệ thống hóa câu trả lời cho câu hỏi của Google PAIR bằng cách tách riêng rủi ro Báo nhầm ở khâu tự chặn và rủi ro Bỏ sót ở khâu phát hiện | Khi giải thích vì sao chọn `Agent`, AI dễ sa vào mô tả tính năng chung chung mà chưa xoáy sâu vào điểm yếu của `Workflow` tĩnh khi gặp hàng chục nguồn log | Viết lập luận sắc bén chỉ rõ `Workflow` tĩnh sẽ thất bại khi phải chọn nhánh động giữa hàng chục nguồn log phân tán và khi cần vòng lặp tự kiểm chứng sau hành động vào ca đêm, đồng thời chốt phạm vi Pilot bắt đầu từ tầng cổng Nginx |

---

## 6. Reflection (CP7)

Trả lời bằng trải nghiệm thật của bạn, tối thiểu 200 từ cho các câu 6.1-6.6 (không tính 6.7, câu này được chấm riêng ở tiêu chí C5). **Không dùng AI để viết thay.**

**6.1. Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Khi nghe Hoàng Vũ trình bày bài toán duyệt câu hỏi trắc nghiệm, Gia Bảo trình bày bài toán truy xuất dữ liệu kinh doanh bằng Text-to-SQL và Hà Anh trình bày bài toán chấm bài code Python cho 75 học sinh, tôi nhận ra điểm chung lớn nhất là cả bốn chúng tôi ban đầu đều rất dễ nhảy thẳng vào việc nghĩ xem mô hình AI sẽ làm gì trước khi bóc tách xem bước nào trong quy trình hiện tại mới thực sự là điểm nghẽn. Những bài toán có quy tắc rõ ràng như kiểm tra lỗi cú pháp Python hay lọc câu hỏi trùng lặp thực chất giải quyết bằng `Rule` (Unit Test, Linter, công thức kiểm tra) vừa rẻ vừa chính xác hơn gọi LLM. Ngược lại, bài toán chỉ thực sự cần đến `Agent` khi đường đi điều tra buộc phải rẽ nhánh linh hoạt qua nhiều nguồn dữ liệu khác nhau tùy theo triệu chứng phát sinh như trong vận hành hạ tầng đa nguồn log.

**6.2. Nhóm có lúc nào bị "solution-first" (nghĩ giải pháp trước khi hiểu vấn đề) không? Lúc đó nhóm nhận ra và xử lý thế nào?**

Có, chính tôi là người rơi vào bẫy solution-first rõ nhất ở giai đoạn đầu. Xuất phát từ mong muốn xây dựng một hệ thống Agentic AI tự chủ hoàn toàn, có lúc tôi đã đặt nặng việc thiết kế cơ chế cho Agent tự động chặn lỗ hổng theo điểm `Confidence Score` trước khi phân tích kỹ xem kỹ sư trực ca đang thực sự mất thời gian ở bước nào và họ sợ rủi ro gì nhất. Khi Bảo và Vũ đặt câu hỏi phản biện ở CP3 và đối chiếu với kết quả phỏng vấn 5 kỹ sư ở CP4, cả nhóm mới nhận ra không thể mặc định cho AI tự chạy lệnh trên hệ thống thật ngay lập tức. Nhóm đã xử lý bằng cách quay lại tách rõ 3 nhánh Opportunity trên cây OST (lọc cảnh báo giả đầu vào, tra chéo nhiều nguồn log, và phản ứng sự cố ngoài giờ), đặt lớp `Rule` lên trước để lọc nhiễu, tách quyền suy luận chỉ đọc (`Read-only`) của Agent khỏi chính sách cấp quyền thực thi, và bắt buộc qua giai đoạn chạy thử `Shadow/read-only` trước.

**6.3. Tôi có đổi ý sau khi bị phản biện không? Kể một lần cụ thể.**

Tôi đã đổi ý ở hai điểm rất cụ thể sau khi nhận phản biện từ nhóm và kết quả kiểm chứng CP4. Thứ nhất, ở bản Card ban đầu tôi ước lượng kỹ sư mất 55-70 phút chỉ để đọc và lọc log (gộp chung thành 90-120 phút mỗi sự cố), đồng thời có lúc diễn đạt dễ gây hiểu nhầm như thể hệ thống chỉ đọc 2 file log Nginx mẫu. Sau khi Bảo chất vấn về định nghĩa các mốc thời gian và Vũ phỏng vấn 5 người làm vận hành thực tế, tôi nhận ra việc khoanh vùng tầng lỗi trong giờ hành chính chỉ mất 15-30 phút, còn nỗi đau lớn nhất nằm ở độ trễ phát hiện và phản ứng vào ban đêm. Tôi đã sửa lại các mục 1, 2.3, 4.1, 4.3 và 6.3 trong báo cáo nhóm để tách bạch hai con số này. Thứ hai, ban đầu tôi nghĩ chỉ cần đặt mốc `Confidence Score >= 85%` là đủ cho phép Agent tự chặn, nhưng sau phản biện tôi đồng ý phải khóa chặt trong `Parameterized Runbook` (cấm sinh lệnh shell tự do), bắt buộc kiểm tra `Whitelist` bằng `Rule` cứng, giới hạn thời gian chặn tối đa 15 phút (`TTL`) và có nút `1-click Rollback`.

**6.4. Kết quả kiểm chứng (phỏng vấn/survey/research) có làm tôi bất ngờ không? Điều gì?**

Điều làm tôi bất ngờ nhất từ 5 buổi phỏng vấn của Vũ là thời gian khoanh vùng tầng gây lỗi thực tế trong giờ làm việc chỉ khoảng 15-30 phút chứ không dài tới 60-90 phút như tôi giả định ban đầu, bởi nhiều nơi đã có sẵn Grafana, Loki hoặc Datadog hỗ trợ một phần. Tuy nhiên, phỏng vấn lại xác nhận rất mạnh nỗi đau ngoài giờ khi có tới 2/5 người thường xuyên bị dựng dậy lúc nửa đêm vì cả sự cố thật lẫn cảnh báo giả, và vẫn phải `ssh` vào từng máy dùng `grep`/`tail` khi cần đào sâu. Ngoài ra, đa số người được hỏi không phản đối việc tự động chặn IP vào ban đêm nhưng kiên quyết đòi hỏi phải có đủ 3 chốt chặn là `Whitelist`, giới hạn thời gian chặn và `Rollback`, khớp hoàn toàn với hướng thiết kế tự chủ có kiểm soát của nhóm.

**6.5. Điều khó nhất khi viết Problem Statement là gì?**

Điều khó nhất là định nghĩa các chỉ số đo lường (`Success Metric`) và ranh giới an toàn (`Boundary`) sao cho không đánh tráo khái niệm và không biến mục tiêu giả thuyết thành kết quả đã kiểm chứng. Thời gian phát hiện sự cố, thời gian khoanh vùng tầng lỗi (15-30 phút) và tổng thời gian từ lúc xuất hiện bất thường đến lúc cô lập xong ngoài giờ là ba đại lượng hoàn toàn khác nhau; nếu lấy baseline 15-30 phút khoanh vùng trong giờ đem so trực tiếp với mục tiêu dưới 5 phút tự động cô lập vào ban đêm thì sẽ sai về mặt phương pháp. Bên cạnh đó, viết `Boundary` đòi hỏi phải cân bằng rất kỹ: nếu cấm hệ thống làm mọi thứ thì không giải quyết được việc kỹ sư bị gọi dậy lúc nửa đêm, nhưng nếu buông lỏng cho LLM tự chấm điểm tự tin rồi tự sinh lệnh thì nguy cơ chặn nhầm khách hàng thật là quá lớn.

**6.6. Nếu làm lại, tôi sẽ đổi gì? Tôi sẽ phản biện nhóm mạnh hơn ở điểm nào?**

Nếu làm lại từ đầu, ngay từ bước viết Problem Card cá nhân tôi sẽ tách riêng thời gian phát hiện trễ ngoài giờ (`MTTD`), thời gian tra chéo log khoanh vùng tầng lỗi (`MTTI`) và thời gian thực thi cô lập (`MTTM`) thay vì gộp chung thành một khoảng 90-120 phút khiến nhóm mất thời gian hiệu chỉnh lại giữa v0 và v1. Tôi cũng sẽ chuẩn bị sẵn một tập 20-30 sự cố mẫu đã ẩn danh từ tầng cổng Nginx để cả nhóm bấm giờ và thử nghiệm công thức tính `Confidence Score` ngay trong buổi lab. Khi phản biện nhóm, tôi sẽ xoáy sâu hơn vào việc yêu cầu kiểm chứng bằng dữ liệu thật đối với mọi con số ngưỡng đề xuất (như mốc 60%, 85% hay tỷ lệ cảnh báo giả dưới 15%) để không ai nhầm lẫn giữa giả thuyết thiết kế với kết quả đã được chứng minh.

**6.7. Hiểu bài:** giải thích bằng 5-8 câu, không nhìn tài liệu, chuỗi *problem -> quy trình -> metric -> boundary -> mức can thiệp AI -> quyết định* của bài nhóm mình.

Problem mà nhóm chọn là kỹ sư trực ca vận hành mất 15-30 phút để lọc nhiễu và tra chéo qua nhiều nguồn log rời rạc nhằm khoanh vùng tầng gây lỗi, đặc biệt vào ngoài giờ hoặc ban đêm thì sự cố bị phát hiện và phản ứng rất trễ trong khi người trực thường xuyên bị dựng dậy bởi cả cảnh báo giả. Quy trình hiện tại gồm 6 bước thủ công từ nhận cảnh báo, mở log cổng vào Nginx, lọc log giữ phiên, tra chéo sang log tường lửa, DNS, ứng dụng, database rồi mới quyết định gõ lệnh cô lập hoặc chuyển giao. Về metric, nhóm tách bạch thời gian khoanh vùng tầng lỗi (baseline phỏng vấn 15-30 phút) với thời gian từ lúc phát sinh bất thường ngoài giờ đến lúc cô lập xong, đặt mục tiêu thử nghiệm dưới 5 phút cho ca đủ điều kiện tự cô lập, dưới 15 phút cho ca chờ người duyệt `HITL`, tỷ lệ cảnh báo sai dưới 15% và 0 lần chặn nhầm kết nối hợp lệ. Về boundary, Agent chỉ được cấp quyền chỉ đọc (`Read-only`) khi truy vấn log, tuyệt đối cấm tự sinh lệnh shell hay tác động vào dịch vụ cốt lõi và dải IP trong `Whitelist`; mọi thao tác tự cô lập ở cổng Nginx chỉ được gọi qua `Parameterized Runbook` định sẵn khi `Confidence Score >= 85%`, có thời hạn tự mở tối đa 15 phút (`TTL`), tự kiểm tra lại sau 2 phút (`Self-Check`) và có nút Hoàn tác 1 chạm (`1-click Rollback`), còn từ 60% đến dưới 85% bắt buộc chuyển sang con người duyệt (`HITL`). Nhóm chọn mức can thiệp lai giữa `Rule` (lọc nhiễu theo chu kỳ và kiểm tra `Whitelist`) với `Agent` có kiểm soát (`Bounded Autonomy`), vì hạ tầng có hàng chục nguồn log phân tán nên đường điều tra phải rẽ nhánh linh hoạt theo từng loại lỗi mà `Workflow` tĩnh cố định không đáp ứng được. Quyết định cuối cùng của nhóm là **Go - triển khai pilot có điều kiện** theo 2 giai đoạn tại tầng cổng Nginx: giai đoạn 1 chạy `Shadow/read-only` trong 2 tuần trên tối thiểu 30 sự cố để hiệu chuẩn `Confidence Score` và kiểm chứng độ chính xác, chỉ khi đạt đủ các cổng an toàn mới mở quyền tự cô lập cục bộ ở giai đoạn 2, và dừng ngay lập tức (quay về `Rule + Workflow read-only + HITL`) nếu có dù chỉ 1 lần vi phạm `Whitelist`/phân quyền hoặc lỗi cơ chế `Rollback`.

---

## 7. Tài liệu tham khảo

- [Đề bài CHECKPOINTS](../../CHECKPOINTS.md)
- [Quy định sử dụng AI](../../RULES.md)
- [Tiêu chí chấm điểm RUBRIC](../../RUBRIC.md)
- Anthropic, *Building Effective Agents*: https://www.anthropic.com/research/building-effective-agents
- Google PAIR, *People + AI Guidebook*: https://pair.withgoogle.com/chapter/user-needs/
- OpenSearch Documentation, *Anomaly Detection Plugin*: https://opensearch.org/docs/latest/monitoring-plugins/ad/index/
- Datadog Documentation, *Watchdog Log Anomaly Detection*: https://docs.datadoghq.com/watchdog/
- GoAccess, *Real-time Web Log Analyzer*: https://goaccess.io/
- Grafana Labs, *Grafana Loki Documentation*: https://grafana.com/docs/loki/latest/
