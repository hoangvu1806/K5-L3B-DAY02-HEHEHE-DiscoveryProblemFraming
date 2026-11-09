# Báo cáo cá nhân — 2A202603887_TranThiHaAnh

> Đổi tên file theo quy tắc `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md` (MSSV trước, dấu `_`, họ tên viết liền không dấu). Sửa cả dòng tiêu đề phía trên cho khớp.
> Template chi tiết và prompt mẫu cho từng mục: [docs/01-worksheet.md](../../docs/01-worksheet.md).
> Mỗi thành viên một file trong `report/individual/` trên repo nhóm: copy template này thành file mới, điền, rồi commit bằng tài khoản GitHub của bạn. Không viết hộ người khác.

## 1. Thông tin học viên

- Họ tên: Trần Thị Hà Anh
- MSSV: 2A202603887
- Email trường (không bắt buộc, repo có thể để public):
- Tên nhóm: HEHEHE
- Link repo nhóm: https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming

---
Scenario: Giáo viên dạy lập trình tại trung tâm

Nhân vật: Minh, 24 tuổi, là giáo viên part-time tại một trung tâm dạy lập trình, phụ trách 5 lớp Python cơ bản, mỗi lớp khoảng 15 học sinh. Mỗi khóa học kéo dài 12 tuần.

Bối cảnh: Sau mỗi buổi học, Minh phải kiểm tra và chấm từng bài code, xác định lỗi sai, viết nhận xét cho học sinh. Nhiều học sinh mắc lỗi tương tự nhau nhưng Minh vẫn phải kiểm tra từng bài thủ công.

Ngoài ra, Minh gặp khó khăn khi tổng hợp lỗi sai phổ biến của cả lớp, theo dõi những kiến thức từng học sinh còn yếu và đánh giá sự tiến bộ qua nhiều buổi học.

Cuối khóa, Minh phải xem lại điểm số, bài tập và ghi chú trong suốt 12 tuần để viết nhận xét cá nhân cho từng học sinh và gửi phụ huynh.

Mục tiêu: Giảm thời gian chấm bài, hỗ trợ phân tích lỗi sai và theo dõi tiến bộ của học sinh, từ đó đưa ra nhận xét chính xác, nhất quán và có căn cứ trong suốt khóa học.

## 2. Scan problem (CP1)

Lăng kính: **Lặp lại** · **Tốn thời gian** · **Cần đọc, tổng hợp nhiều thông tin** · **Pain từ người khác**.

| # | Lăng kính | Job Story: Khi… tôi muốn… để… | Ai chịu ảnh hưởng? | Dấu hiệu thật (thời gian, tần suất, số người, bằng chứng) |
|---:|---|---|---|---|
| 1 | Lặp lại | Khi kết thúc mỗi buổi học Python, tôi muốn kiểm tra từng bài code theo cùng một bộ tiêu chí, để trả kết quả cho học sinh mà không bỏ sót lỗi | Minh; khoảng 75 học sinh của 5 lớp | 5 lớp × khoảng 15 học sinh = khoảng 75 bài cho mỗi vòng bài tập; việc chấm lặp lại sau mỗi buổi học (theo scenario) |
| 2 | Tốn thời gian | Khi chấm một loạt bài có nhiều lỗi giống nhau, tôi muốn xác định nhanh lỗi và nguyên nhân trong từng bài, để dành thời gian cho những trường hợp cần giải thích riêng | Minh | Nhiều học sinh mắc lỗi tương tự nhưng Minh vẫn kiểm tra từng bài thủ công; ước tính 5 phút/bài tương đương 375 phút cho 75 bài|
| 3 | Lặp lại | Khi nhiều học sinh mắc cùng một lỗi, tôi muốn viết nhận xét nhất quán nhưng vẫn đúng với bài của từng em, để các em biết chính xác cần sửa gì | Minh; học sinh | Khoảng 75 bài/vòng; nhận xét phải viết riêng cho từng bài dù lỗi lặp lại; khoảng 2 phút/bài tương đương 150 phút cho 75 bài|
| 4 | Cần đọc, tổng hợp nhiều thông tin | Khi chấm xong bài của một lớp, tôi muốn biết những lỗi nào xuất hiện nhiều nhất, để điều chỉnh nội dung ôn tập cho buổi sau | Minh; khoảng 15 học sinh/lớp | Minh phải tổng hợp lỗi phổ biến của 5 lớp, mỗi lớp khoảng 15 học sinh; hiện làm thủ công  |
| 5 | Cần đọc, tổng hợp nhiều thông tin | Khi chuẩn bị dạy buổi tiếp theo, tôi muốn biết học sinh nào còn yếu ở từng kiến thức, để chọn ví dụ và bài luyện phù hợp | Minh; học sinh cần hỗ trợ | Phải đối chiếu bài làm, lỗi sai và ghi chú qua nhiều buổi; mỗi khóa kéo dài 12 tuần |
| 6 | Tốn thời gian | Khi cần đánh giá sự tiến bộ của một học sinh, tôi muốn xem được lỗi cũ, lỗi đã khắc phục và lỗi còn lặp lại, để không đánh giá chỉ dựa trên bài gần nhất | Minh; từng học sinh; phụ huynh | Cần theo dõi khoảng 15 học sinh/lớp qua 12 tuần; scenario nêu khó khăn khi đánh giá tiến bộ qua nhiều buổi |
| 7 | Cần đọc, tổng hợp nhiều thông tin | Khi kết thúc khóa học, tôi muốn tổng hợp điểm số, bài tập và ghi chú của từng học sinh, để viết nhận xét cá nhân có căn cứ cho phụ huynh | Minh; học sinh; phụ huynh | 5 lớp × khoảng 15 học sinh = khoảng 75 nhận xét; mỗi nhận xét phải xem lại dữ liệu trong 12 tuần |
| 8 | Pain từ người khác | Khi nhận phản hồi sau bài tập, học sinh và phụ huynh muốn biết lỗi cụ thể và sự tiến bộ theo thời gian, để hiểu nên cải thiện kiến thức nào | Học sinh; phụ huynh; Minh | Khoảng 75 học sinh và gia đình nhận phản hồi; mục tiêu trong scenario yêu cầu nhận xét chính xác, nhất quán và có căn cứ; chưa có phỏng vấn để xác nhận mức độ pain |

**Nếu có dùng AI để gợi ý thêm:** AI được dùng để mở rộng scenario theo 4 lăng kính. Giữ lại ý #6 và #8 vì chúng vẫn mô tả nhu cầu có actor, bối cảnh và kết quả rõ ràng. Bỏ ý “dùng AI tự động chấm toàn bộ bài và gửi điểm” vì đó là giải pháp, chưa phải problem và có rủi ro gửi kết quả sai khi giáo viên chưa kiểm tra.

---

## 3. Top 3 Problem Cards + quy trình nháp (CP2)

### Bảng chọn top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---:|---|---|---|
| 1 | Chấm code và viết phản hồi cho từng bài (#1–#3) | Tần suất cao, quy trình rõ, số lượng khoảng 75 bài cho mỗi vòng bài tập và có bước nghẽn cụ thể | Tỷ lệ bài có lỗi lặp lại chưa được đo |
| 2 | Tổng hợp lỗi phổ biến của từng lớp (#4) | Tác động trực tiếp tới việc điều chỉnh bài giảng; phải gom dữ liệu từ khoảng 15 bài/lớp | Taxonomy lỗi có ổn định giữa các bài tập hay không và baseline 20 phút/lớp chưa được đo |
| 3 | Theo dõi tiến bộ và viết nhận xét cuối khóa (#5–#7) | Phải tổng hợp dữ liệu của khoảng 75 học sinh trong 12 tuần; ảnh hưởng tới học sinh và phụ huynh | Tiêu chí thế nào là “tiến bộ”|

### Problem Card #1

| Trường | Nội dung |
|---|---|
| Job Story | Khi kết thúc mỗi buổi học Python, tôi muốn kiểm tra từng bài code và viết phản hồi đúng với lỗi của từng em, để học sinh biết cách sửa mà tôi vẫn trả bài kịp thời |
| Actor | Minh |
| Thời điểm / bối cảnh | Sau mỗi buổi học, khi Minh nhận bài tập code của lớp và cần trả phản hồi trước buổi kế tiếp |
| Quy trình hiện tại (3–7 bước) | 1. Mở bài nộp · 2. Chạy code/test thủ công · 3. Đối chiếu yêu cầu · 4. Xác định lỗi và nguyên nhân · 5. Viết nhận xét riêng · 6. Ghi điểm · 7. Chuyển sang bài tiếp theo |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 4–5: xác định nguyên nhân rồi diễn đạt phản hồi; ước tính 3 phút trong tổng 5 phút mỗi bài |
| Impact (nếu không giải thì sao) | Với khoảng 75 bài/vòng, tổng thời gian ước tính 375 phút; phản hồi có thể chậm hoặc thiếu nhất quán, Minh còn ít thời gian chuẩn bị bài dạy |
| Success metric (baseline → target) | Thời gian trung bình ước tính dưới 3 phút/bài; 100% bài vẫn được Minh kiểm tra trước khi trả; tỷ lệ phản hồi phải sửa do xác định sai lỗi dưới 5%. Đo bằng bấm giờ và log sửa trong 3 vòng bài tập |
| Phương án không dùng AI | Bộ test tự động cho yêu cầu có đúng/sai rõ ràng + rubric + thư viện nhận xét mẫu theo nhóm lỗi; Minh chọn và cá nhân hóa phản hồi |
| Giả thuyết về AI (nếu có) | Sau khi rule/test cho kết quả, AI có thể gợi ý giải thích lỗi và bản nháp nhận xét từ code, yêu cầu bài tập và rubric; Minh kiểm tra trước khi gửi |
| Cảm nhận nhanh | Workflow |

Quy trình nháp hiện tại:

```text
HIỆN TẠI — khoảng 5 phút/bài (ước tính cần kiểm chứng)

[1 Mở bài: 0,5'] → [2 Chạy code/test: 1'] → [3 Đối chiếu yêu cầu: 0,5']
→ [4 Xác định lỗi và nguyên nhân: 1,5'] ← BOTTLENECK
→ [5 Viết nhận xét: 1,5'] ← BOTTLENECK → [6 Ghi điểm/chuyển bài]
```

### Problem Card #2

| Trường | Nội dung |
|---|---|
| Job Story | Khi chấm xong bài của một lớp, tôi muốn tổng hợp các lỗi xuất hiện nhiều nhất, để điều chỉnh phần ôn tập và bài luyện cho buổi sau |
| Actor | Minh |
| Thời điểm / bối cảnh | Sau khi chấm xong một vòng bài tập của một lớp, trước lúc soạn buổi học tiếp theo |
| Quy trình hiện tại (3–7 bước) | 1. Xem lại nhận xét của từng bài · 2. Ghi các lỗi đáng chú ý · 3. Chuẩn hóa tên lỗi giống nhau · 4. Đếm số học sinh theo lỗi · 5. Xếp lỗi theo mức phổ biến · 6. Chọn nội dung cần ôn lại |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 1–4: đọc lại, chuẩn hóa và đếm lỗi từ khoảng 15 bài; ước tính 20 phút/lớp, cần đo thực tế |
| Impact (nếu không giải thì sao) | Với 5 lớp, ước tính khoảng 100 phút cho mỗi vòng tổng hợp; Minh có thể bỏ sót pattern và chọn nội dung ôn tập dựa vào trí nhớ |
| Success metric (baseline → target) | Thời gian tổng hợp ước tính 20 → dưới 5 phút/lớp; danh sách phải bao phủ ít nhất 90% lỗi đã được Minh đánh dấu khi chấm; Minh xác nhận nhóm lỗi trước khi dùng. Đo trong 3 vòng bài tập |
| Phương án không dùng AI | Dùng taxonomy lỗi cố định và form/dropdown khi chấm; bảng tính tự đếm tần suất và xếp hạng theo công thức |
| Giả thuyết về AI (nếu có) | AI chỉ đề xuất gom các nhận xét chưa khớp taxonomy vào nhóm lỗi; Minh duyệt tên nhóm, còn việc đếm do rule thực hiện |
| Cảm nhận nhanh | Rule; chỉ cân nhắc Workflow nếu lỗi tự do khó chuẩn hóa |

Quy trình nháp hiện tại:

```text
HIỆN TẠI — khoảng 20 phút/lớp (ước tính cần kiểm chứng)

[1 Đọc lại nhận xét 15 bài: 8'] → [2 Ghi lỗi: 4']
→ [3 Chuẩn hóa các cách gọi lỗi: 4'] ← BOTTLENECK
→ [4 Đếm tần suất: 2'] → [5 Xếp hạng + chọn nội dung ôn: 2']
```

### Problem Card #3

| Trường | Nội dung |
|---|---|
| Job Story | Khi kết thúc khóa 12 tuần, tôi muốn xem lại điểm, bài tập, lỗi sai và sự tiến bộ của từng học sinh, để viết nhận xét cá nhân chính xác và có căn cứ cho phụ huynh |
| Actor | Minh; khoảng 75 học sinh; phụ huynh nhận báo cáo cuối khóa |
| Thời điểm / bối cảnh | Cuối mỗi khóa, sau tuần 12, khi Minh phải hoàn thành nhận xét cho từng học sinh |
| Quy trình hiện tại (3–7 bước) | 1. Mở bảng điểm · 2. Tìm lại bài và ghi chú của học sinh · 3. Đọc dữ liệu qua 12 tuần · 4. So sánh lỗi đầu kỳ/cuối kỳ · 5. Chọn dẫn chứng · 6. Viết và rà soát nhận xét · 7. Gửi phụ huynh |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 2–5: tìm, đọc và tổng hợp bằng chứng qua 12 tuần; ước tính 10 phút trong tổng 15 phút cho mỗi học sinh, cần bấm giờ để kiểm chứng |
| Impact (nếu không giải thì sao) | Ở mức ước tính 15 phút/học sinh, 75 nhận xét cần khoảng 18,75 giờ cuối khóa; nhận xét dễ chung chung hoặc bỏ sót tiến bộ và lỗi còn lặp lại |
| Success metric (baseline → target) | Tổng thời gian ước tính 15 → dưới 7 phút/học sinh; 100% nhận xét có ít nhất 2 dẫn chứng truy được về tuần/bài cụ thể; không cho phép nhận xét gửi khi Minh chưa duyệt. Đo ở một lớp pilot cuối khóa |
| Phương án không dùng AI | Chuẩn hóa sổ theo dõi theo tuần, dùng mã kỹ năng/mã lỗi và template nhận xét; bảng tính tạo biểu đồ tiến bộ và truy xuất dẫn chứng |
| Giả thuyết về AI (nếu có) | AI tạo bản nháp nhận xét từ dữ liệu 12 tuần đã cấu trúc, nêu điểm tiến bộ, điểm cần cải thiện và dẫn chứng; Minh đối chiếu rồi sửa trước khi gửi |
| Cảm nhận nhanh | Workflow |

Quy trình nháp hiện tại:

```text
HIỆN TẠI — khoảng 15 phút/học sinh (ước tính cần kiểm chứng)

[1 Mở bảng điểm: 1'] → [2 Tìm bài + ghi chú 12 tuần: 4']
→ [3 Đọc và so sánh tiến bộ: 4'] ← BOTTLENECK
→ [4 Chọn dẫn chứng: 2'] → [5 Viết nhận xét: 3'] → [6 Rà soát: 1']
```

### Card muốn pitch nhất

- Card số: 1.
- Vì sao: Pain xảy ra sau mỗi buổi học, có khối lượng lớn và quy trình lặp lại rõ. Card này cũng cho phép tách phần có đúng/sai rõ ràng cho rule/test và phần giải thích lỗi cần ngữ cảnh, trong khi giáo viên vẫn giữ quyền quyết định điểm và phản hồi cuối cùng.
- Câu hỏi muốn nhóm phản biện: Bottleneck thật nằm ở chạy/kiểm tra code, xác định nguyên nhân lỗi hay viết phản hồi; và baseline 5 phút/bài có đúng khi bấm giờ trên bài thật không?

### AI đã phản biện card thế nào

| Điểm yếu AI chỉ ra | Đồng ý? | Đã sửa gì |
|---|---|---|
| Khối lượng 75 bài và các mốc 5, 20, 15 phút mới được suy ra từ scenario, chưa phải dữ liệu Minh đã đo | Đồng ý | Giữ các con số dưới dạng ước tính; tại success metric nêu cách kiểm chứng bằng bấm giờ/log trong 3 vòng bài tập hoặc một lớp pilot |
| Card #1 đang gọi cả bước xác định nguyên nhân và viết nhận xét là bottleneck, nên chưa biết bước nào thực sự nghẽn hơn | Đồng ý | Tách quy trình “chấm bài” thành các bước nhỏ và ghi riêng 1,5 phút cho mỗi bước; giữ câu hỏi này để nhóm phản biện và xác nhận bằng bấm giờ trên bài thật |
| Metric của Card #1 không nên chỉ đo tốc độ vì phản hồi nhanh nhưng sai vẫn là thất bại | Đồng ý | Bổ sung hai ràng buộc chất lượng: 100% bài được Minh kiểm tra trước khi trả và tỷ lệ phản hồi phải sửa do xác định sai lỗi dưới 5% |
| Card #2 có đầu vào và cách đếm khá rõ, nên dùng AI cho toàn bộ quy trình có thể phức tạp quá mức cần thiết | Đồng ý | Chọn Rule làm cảm nhận nhanh: taxonomy lỗi + form/dropdown + công thức đếm; AI chỉ được cân nhắc để đề xuất nhóm cho nhận xét chưa khớp taxonomy |
| Khái niệm “tiến bộ” ở Card #3 còn mơ hồ; nếu không có dẫn chứng, nhận xét cuối khóa dễ trở thành nhận định chung chung | Đồng ý | Yêu cầu mỗi nhận xét có ít nhất hai dẫn chứng truy được về tuần/bài cụ thể và thử đo trên một lớp pilot trước khi áp dụng cho cả 5 lớp |
| Có thể để AI tự chấm điểm hoặc tự gửi phản hồi để tiết kiệm thêm thời gian | Không đồng ý | Giữ quyền quyết định cho Minh: AI chỉ tạo gợi ý/bản nháp; Minh phải đối chiếu, sửa và duyệt trước khi phản hồi đến học sinh hoặc phụ huynh |

---

## 4. Tôi đã tham gia phần nào (CP3 → CP7)

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng tới bài nhóm |
|---|---|---|
| Pitch Problem Card | Pitch 3 candidate: chấm code và viết phản hồi (#10), tổng hợp lỗi lớp (#11), nhận xét cuối khóa (#12) | Nhóm đưa cả 3 vào Cluster B (EdTech); candidate #10 vào shortlist và đạt 26/35 |
| Phản biện bài của bạn khác | Câu hỏi tôi đã đặt: Có nên gộp Card #2–#3 của Nguyên thành các mắt xích của Card #1? Tiêu chí định lượng cho phương án nhiễu tốt là gì? Người không biết SQL kiểm tra truy vấn bằng cách nào? | Giúp làm rõ quy trình AIOps trọn vẹn, yêu cầu eval cho bài trắc nghiệm và boundary kiểm chứng của Text-to-SQL |
| Nhận phản biện | Tôi được hỏi: Unit Test/Linter đã bắt phần lớn lỗi code chưa; mã lỗi + Excel có đủ cho thống kê không; việc cuối khóa có đủ cấp thiết không? | Tôi đồng ý phần lỗi xác định và thống kê nên ưu tiên Rule/No AI; không tiếp tục giả định AI cần cho toàn bộ quy trình chấm bài |
| Gom cluster / cây OST | Cung cấp 3 candidate để nhóm gom vào Cluster B; đối chiếu chúng với cluster AIOps và Text-to-SQL | Nhìn rõ candidate của tôi có quy trình rõ nhưng phần lớn giải được bằng Rule/Workflow, không cần Agent |
| Chọn candidate problem | Tham gia so sánh shortlist; chấp nhận chọn bài điều tra log đa tầng của Nguyên thay cho candidate #10 của tôi | Candidate AIOps thể hiện rõ hơn sự khác nhau giữa Rule, Workflow và Agent, nhưng cần boundary chặt |
| Kiểm chứng / research | Đọc tổng hợp 5 phỏng vấn; kiểm tài liệu chính thức của Datadog Watchdog, Dynatrace Davis AI và PagerDuty AIOps/Event Orchestration | Hoàn thiện mục 3.3, chỉ ra công cụ giải bước nào, điều kiện dữ liệu và khoảng trống so với auto-containment |
| Quy trình nhóm | Không phụ trách vẽ chính; dùng quy trình hiện tại/tương lai để xác định chỗ Rule, Agent read-only, policy và HITL | Quyết định/threshold bám đúng điểm can thiệp và fallback trong mục 4 báo cáo nhóm |
| Problem Statement | Đối chiếu v1 với CP4: baseline khoanh vùng 15–30 phút, chưa có baseline phát hiện → cô lập ngoài giờ | Không coi target <5/<15 phút hoặc ngưỡng 60/85 là kết quả đã kiểm chứng |
| Mức can thiệp AI | Phản biện rủi ro của quyền tự động thực thi khi score chưa hiệu chuẩn | Tách Agent điều tra/đề xuất khỏi Rule/policy cấp quyền; trước mắt chỉ shadow pilot read-only |
| Quyết định | Đánh giá 4 rủi ro và viết quyết định, pilot, tiêu chí mở quyền, ngưỡng dừng | Chốt Go — pilot có điều kiện theo hai giai đoạn; quay về Rule + Workflow read-only + HITL nếu không đạt hoặc có sự cố an toàn |

---

## 5. Dùng AI

| Checkpoint | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai hoặc hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| CP1 Scan | Gợi ý thêm problem theo 4 lăng kính | Mở rộng sang theo dõi tiến bộ và pain của phụ huynh | Gợi ý “AI tự động chấm và gửi điểm” là solution-first và bỏ qua rủi ro sai | Giữ Job Story có actor/bối cảnh/kết quả; bỏ giải pháp tự gửi và ghi rõ các số là ước tính từ scenario |
| CP2 Problem Card | Yêu cầu phản biện 3 card, không viết lại thay | Chỉ ra baseline chưa đo, bottleneck Card #1 bị gộp và metric chỉ đo tốc độ là thiếu | Có gợi ý tăng tự động hóa bằng tự chấm/tự gửi phản hồi | Tách bước 4–5, thêm log sửa sai và giữ Minh là người duyệt cuối; Card #2 chọn Rule thay vì AI |
| CP4 Research | Hỗ trợ tìm và so sánh tài liệu chính thức của 3 công cụ | Nhanh chóng định vị các trang về baseline/RCA, topology và event orchestration | Bản nháp ban đầu suy diễn “chi phí rất cao”, “bắt buộc đưa toàn bộ log lên cloud” và gán HITL/rollback cho sản phẩm khi chưa có nguồn trực tiếp | Chỉ giữ claim được tài liệu hãng hỗ trợ; nêu rõ điều kiện APM/topology/event input và tách bài học thiết kế của nhóm khỏi tính năng sản phẩm |
| CP5 Quy trình | Không dùng AI trực tiếp để vẽ quy trình | — | — | Tôi đọc quy trình nhóm để gắn risk và ngưỡng dừng vào đúng bước |
| CP5–6 Problem Statement | Dùng AI rà tính nhất quán giữa kết quả phỏng vấn, baseline và target | Phát hiện 15–30 phút là thời gian khoanh vùng, không đồng nghĩa 90–120 phút phát hiện → cô lập | AI có thể trình bày target đề xuất như số đã được kiểm chứng | Ghi rõ target/ngưỡng score là giả thuyết; yêu cầu đo timestamp cùng định nghĩa trong shadow pilot |
| CP6 Mức can thiệp / quyết định | Gợi ý lỗ hổng rủi ro và các ngưỡng pilot có thể đo | Hữu ích khi tách Value/Usability/Feasibility/Viability và xây kill criteria | Có xu hướng coi các guardrail trên giấy là đủ để triển khai production dù chưa có log pilot hay thử rollback | Tôi chốt Go cho pilot có điều kiện, không phải Go production: shadow/read-only trước, chỉ mở quyền cục bộ khi đạt cổng an toàn và dừng ngay nếu có một vi phạm nghiêm trọng |

---

## 6. Reflection (CP7)

Trả lời bằng trải nghiệm thật của bạn, tối thiểu 200 từ cho các câu 6.1–6.6 (không tính 6.7, câu này được chấm riêng ở tiêu chí C5). **Không dùng AI để viết thay.**

**6.1. Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Khi nghe các bạn pitch, tôi chú ý nhất đến bài toán AIOps của Nhật Nguyên và Text-to-SQL của Gia Bảo. Bài AIOps cho tôi thấy đường điều tra có thể thay đổi theo loại sự cố nên Agent có thể hữu ích, nhưng quyền của Agent phải được giới hạn. Bài Text-to-SQL giúp tôi nhận ra một thử thách kỹ thuật chỉ có giá trị khi gắn với pain thật của người dùng nghiệp vụ. Từ đó, tôi hiểu rằng trước khi so sánh candidate, nhóm phải tách problem khỏi solution, xác định rõ actor, thời điểm xảy ra pain và một bottleneck đo được. Candidate có điểm cao vẫn có thể không được chọn nếu bằng chứng còn yếu hoặc mức can thiệp không phù hợp.

**6.2. Nhóm có lúc nào bị "solution-first" (nghĩ giải pháp trước khi hiểu vấn đề) không? Lúc đó nhóm nhận ra và xử lý thế nào?**

Nhóm đã có lúc solution-first khi gọi tên Agentic AI và Confidence Score trước khi xác nhận bottleneck và baseline. Ý tưởng tự chặn IP cũng xuất hiện trước khi nhóm hỏi người dùng chấp nhận tự động hóa trong điều kiện nào. Ngoài ra, con số 90–120 phút ban đầu được dùng như baseline dù chưa phân biệt thời gian phát hiện, khoanh vùng, cô lập và khắc phục. Nhóm xử lý bằng cách quay lại vẽ quy trình hiện tại, tách từng bottleneck và đối chiếu 5 phỏng vấn. Sau kiểm chứng, pain được chuyển trọng tâm sang phản ứng ngoài giờ và cảnh báo giả. Nhóm cũng so sánh No AI, Rule, Workflow và Agent, rồi thu hẹp pilot ở Nginx với HITL, whitelist, TTL và rollback.

**6.3. Tôi có đổi ý sau khi bị phản biện không? Kể một lần cụ thể.**

Ban đầu tôi nghĩ việc chấm code, viết nhận xét và tổng hợp lỗi của lớp nên sử dụng AI nhiều hơn. Khi nhận câu hỏi phản biện về Unit Test, Linter, taxonomy lỗi và Excel, tôi nhận ra phần lớn bước xác định trước có thể giải bằng Rule hoặc công cụ không dùng AI. Với tổng hợp lỗi, nếu giáo viên gắn mã lỗi ngay lúc chấm thì bảng tính đã có thể đếm tần suất. Vì vậy tôi đổi từ giả thuyết dùng AI cho toàn bộ quy trình sang phương án tách rõ: Rule xử lý phần có tiêu chí xác định, còn AI nếu dùng chỉ hỗ trợ giải thích hoặc soạn nháp và giáo viên vẫn duyệt kết quả cuối cùng.

**6.4. Kết quả kiểm chứng (phỏng vấn/survey/research) có làm tôi bất ngờ không? Điều gì?**

Điều làm tôi bất ngờ là thời gian khoanh vùng được người tham gia phỏng vấn nêu thường chỉ 15–30 phút, không xác nhận giả định 60–90 hoặc 90–120 phút ban đầu. Ngược lại, 2/5 người thường xuyên bị gọi dậy ban đêm, cho thấy pain ngoài giờ quan trọng hơn việc đọc log trong giờ hành chính. Đa số chấp nhận auto-block nhưng chỉ khi có whitelist, rollback và giới hạn thời gian. Khi research, tôi cũng thấy Datadog, Dynatrace và PagerDuty đã hỗ trợ anomaly detection, RCA hoặc orchestration, nhưng các khả năng đó không tự chứng minh rằng Agent nên được quyền thay đổi production. Kết quả này khiến tôi thận trọng hơn khi phân biệt khả năng phân tích với quyền thực thi.

**6.5. Điều khó nhất khi viết Problem Statement là gì?**

Điều khó nhất là giữ cho metric và bằng chứng không bị đánh tráo. Thời gian phát hiện, khoanh vùng, cô lập và khắc phục là những đại lượng khác nhau; không thể lấy baseline của một đại lượng để so với target của đại lượng khác. Nhóm cũng phải ghi rõ các ngưỡng dưới 5 phút, dưới 15 phút, false-alert dưới 15% và Confidence Score 60/85 là mục tiêu đề xuất, chưa phải kết quả đã đạt. Bên cạnh tốc độ, metric phải bảo vệ chất lượng và an toàn. Boundary cũng phải cụ thể: AI không được chạy shell tự do, không chạm whitelist hoặc dịch vụ lõi, và phải chuyển HITL khi chưa đủ điều kiện.

**6.6. Nếu làm lại, tôi sẽ đổi gì? Tôi sẽ phản biện nhóm mạnh hơn ở điểm nào?**

Nếu làm lại, tôi sẽ thu thập timestamp và log của incident thật trước khi chốt baseline, đồng thời thống nhất từ đầu định nghĩa phát hiện, khoanh vùng, cô lập và khắc phục. Tôi sẽ phản biện mạnh hơn lý do chọn Agent thay vì Workflow, yêu cầu công thức Confidence Score và lý do chọn các ngưỡng 60/85. Tôi cũng sẽ đề nghị chuẩn bị kiểm thử staging cho whitelist, RBAC, TTL, rollback và kill switch sớm hơn. Với candidate chấm bài của mình, tôi sẽ bấm giờ trên bài thật và thử Unit Test, Linter, taxonomy lỗi hoặc Excel trước khi đề xuất AI. Cách làm này giúp quyết định mức can thiệp dựa trên bằng chứng thay vì mức độ hấp dẫn của giải pháp.

**6.7. Hiểu bài:** giải thích bằng 5–8 câu, không nhìn tài liệu, chuỗi *problem → quy trình → metric → boundary → mức can thiệp AI → quyết định* của bài nhóm mình.

Problem nhóm chọn là phản ứng sự cố ngoài giờ bị chậm vì cảnh báo giả và nhiều nguồn log làm kỹ sư khó khoanh vùng an toàn. Quy trình bắt đầu từ nhận alert, lọc nhiễu, tra chéo nguồn log, xác định nguyên nhân khả dĩ, cô lập hoặc escalation, rồi hậu kiểm. Nhóm đo riêng thời gian phát hiện, khoanh vùng và cô lập, đồng thời theo dõi false-alert rate, Top-3 root-cause hit rate và số lần chặn nhầm. Boundary là không cho AI chạy shell tự do, không chạm whitelist hoặc dịch vụ lõi; mọi hành động phải dùng runbook định trước, có HITL, TTL, audit và rollback. Mức can thiệp được chọn là Rule để lọc nhiễu kết hợp Agent có giới hạn để chọn hướng điều tra, còn policy, runbook và con người kiểm soát quyền thực thi. Quyết định cuối là Go cho pilot có điều kiện: chạy shadow/read-only trước và chỉ mở auto-containment cục bộ khi đạt các cổng an toàn; nếu vi phạm ngưỡng dừng thì quay về Rule + Workflow read-only + HITL.
---

## 7. Tài liệu tham khảo

- Datadog, [Watchdog](https://docs.datadoghq.com/watchdog/) và [Watchdog RCA](https://docs.datadoghq.com/watchdog/rca/).
- Dynatrace, [Davis AI](https://docs.dynatrace.com/docs/semantic-dictionary/model/davis) và [Root cause analysis concepts](https://docs.dynatrace.com/docs/dynatrace-intelligence/root-cause-analysis-classic/concepts).
- PagerDuty, [AIOps](https://support.pagerduty.com/main/docs/aiops) và [Event Orchestration](https://support.pagerduty.com/main/docs/event-orchestration).
