# Báo cáo cá nhân — 2A202603914_TranGiaBao

## 1. Thông tin học viên

- Họ tên: Trần Gia Bảo
- MSSV: 2A202603914
- Email trường: 26ai.baotg@vinuni.edu.vn
- Tên nhóm: HEHEHE
- Link repo nhóm: https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming

---

## 2. Scan problem (CP1)

**Bối cảnh:** Tôi từng tham gia dự án kết nối AI chạy local với cơ sở dữ liệu khách hàng. Mục tiêu của hệ thống là cho phép người dùng đặt câu hỏi bằng ngôn ngữ tự nhiên, hệ thống chuyển thành truy vấn SQL và trả lại dữ liệu phục vụ phân tích. Trong phần này, tôi tách bài toán người dùng khỏi giải pháp Text-to-SQL: điều cần tìm hiểu trước là những bước nào trong việc tra cứu và phân tích dữ liệu hiện tại đang gây khó khăn.

| # | Lăng kính | Job Story | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---:|---|---|---|---|
| 1 | Tốn thời gian | Khi cần xem doanh thu theo tháng hoặc theo nhóm sản phẩm, tôi muốn lấy được số liệu từ cơ sở dữ liệu mà không phải nhờ developer viết từng câu SQL, để chủ động kiểm tra tình hình kinh doanh. | Quản lý, nhân viên kinh doanh, người phụ trách dữ liệu | Cần xác minh khách đã từng nhờ kỹ thuật xuất báo cáo bao nhiêu lần và mất bao lâu. |
| 2 | Đọc, tổng hợp nhiều thông tin | Khi một chỉ số kinh doanh thay đổi, tôi muốn đối chiếu dữ liệu từ nhiều bảng liên quan, để hiểu chỉ số đó đến từ nhóm khách hàng, đơn hàng hoặc sản phẩm nào. | Người phân tích kinh doanh, quản lý | Cần kiểm tra những báo cáo thực tế có phép JOIN/tổng hợp nhiều bảng và thời gian xử lý. |
| 3 | Pain từ người khác | Khi yêu cầu một báo cáo dữ liệu, tôi muốn hai người cùng hiểu đúng ý nghĩa các trường như doanh thu, đơn hủy và khách hàng mới, để tránh nhận kết quả không đúng câu hỏi ban đầu. | Người yêu cầu báo cáo, developer, data analyst | Cần đối chiếu các lần làm rõ yêu cầu, sửa câu truy vấn hoặc sửa báo cáo trong dự án. |
| 4 | Lặp lại | Khi cần theo dõi cùng một chỉ số theo ngày hoặc theo tuần, tôi muốn có kết quả cập nhật mà không phải nhờ tạo lại báo cáo từ đầu. | Quản lý, vận hành | Cần xác minh tần suất yêu cầu số liệu lặp lại và có dashboard/báo cáo tự động hay chưa. |
| 5 | Tốn thời gian | Khi người dùng hỏi dữ liệu bằng câu thông thường, tôi muốn hệ thống hiểu đúng tên bảng, cột và quan hệ dữ liệu, để không phải sửa truy vấn nhiều lần. | Developer triển khai Text-to-SQL, người sử dụng | Quan sát trực tiếp từ dự án tích hợp AI local; cần bổ sung test case thực tế và tỷ lệ truy vấn sinh đúng. |
| 6 | Lặp lại | Khi kết nối một mô hình AI local với cơ sở dữ liệu của khách, tôi muốn kiểm soát truy vấn được phép chạy, để tránh thao tác sai hoặc lộ dữ liệu nhạy cảm. | Developer, quản trị hệ thống, khách hàng | Cần kiểm tra cấu hình quyền của tài khoản DB, log truy vấn và các tình huống bị chặn. |
| 7 | Đọc, tổng hợp nhiều thông tin | Khi một câu hỏi được diễn đạt theo nhiều cách, tôi muốn nhận kết quả nhất quán và có thể kiểm tra nguồn dữ liệu, để tin tưởng số liệu dùng ra quyết định. | Người dùng nghiệp vụ, người kiểm tra dữ liệu | Cần thử các cách diễn đạt tương đương và so sánh SQL/kết quả với truy vấn chuẩn. |
| 8 | Pain từ người khác | Khi khách hàng muốn chạy AI trên hạ tầng nội bộ, tôi muốn biết rõ giới hạn phần cứng, tốc độ phản hồi và cách phân quyền, để triển khai được mà không phụ thuộc gửi dữ liệu lên dịch vụ ngoài. | IT khách hàng, developer, quản trị bảo mật | Cần bổ sung thông số máy local, thời gian phản hồi và yêu cầu bảo mật thực tế nếu được phép công khai. |

**Phân loại bằng chứng:** Dấu hiệu ở các dòng #1–#4, #7–#8 hiện chủ yếu là **câu hỏi cần xác minh**, không phải số liệu đã ghi nhận. Dòng #5–#6 gắn với đầu việc kỹ thuật từ dự án đã tham gia nhưng chưa kèm log/test case có thể công khai. Vì vậy **không coi 8 dòng đều đã có bằng chứng đo được**; chỉ được bổ sung baseline sau khi kiểm tra dữ liệu thật, ẩn danh và được phép chia sẻ. Đối với từng Job Story, cách đo được đề xuất là số yêu cầu/tuần, thời gian chờ từ yêu cầu đến khi có kết quả, số vòng sửa SQL, tỷ lệ truy vấn đúng theo bộ test và số sự kiện bị chặn do phân quyền.

**Phân biệt phạm vi trải nghiệm:** Tôi có trải nghiệm triển khai bài toán Text-to-SQL và cấu hình AI local. Các tình huống liên quan đến việc nhân viên kinh doanh phải chờ báo cáo, cách họ xem doanh thu hoặc việc báo cáo bị hiểu sai là **giả thuyết về người dùng**, cần xác nhận qua trao đổi hoặc dữ liệu công việc; không xem đây là bằng chứng khách đã gặp.

**Ý tưởng cần loại:** “Xây chatbot AI phân tích mọi dữ liệu doanh nghiệp” là một mô tả giải pháp quá rộng. Tôi giới hạn từng vấn đề vào một tác vụ, một người sử dụng và một đầu ra có thể đo được.

---

## 3. Top 3 Problem Cards (CP2)

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---:|---|---|---|
| 1 | Tự lấy số liệu kinh doanh mà không phụ thuộc viết SQL (#1) | Liên quan trực tiếp tới mục tiêu của dự án Text-to-SQL, có thể kiểm tra thời gian và độ chính xác | Khách đã có BI/dashboard hoặc truy vấn mẫu đáp ứng đủ nhu cầu chưa? |
| 2 | Hiểu đúng cấu trúc CSDL khi chuyển câu hỏi thành SQL (#5) | Có thể xây bộ test từ schema và truy vấn đúng để đo | Lỗi chủ yếu đến từ schema, prompt hay mô hình local? |
| 3 | Kết quả phân tích nhất quán và có thể kiểm chứng (#7) | Có ảnh hưởng trực tiếp tới độ tin cậy của công cụ | Mức sai lệch hiện tại là bao nhiêu, người dùng kiểm bằng cách nào? |

### Problem Card #1 — Truy xuất số liệu bằng ngôn ngữ tự nhiên

| Trường | Nội dung |
|---|---|
| Job Story | Khi cần biết doanh thu, số đơn hoặc hiệu quả theo giai đoạn, tôi muốn tự hỏi và lấy dữ liệu từ hệ thống, để không phải chờ người biết SQL xuất báo cáo. |
| Actor | Quản lý hoặc nhân viên nghiệp vụ có quyền xem dữ liệu nhưng không sử dụng SQL |
| Thời điểm / bối cảnh | Khi cần câu trả lời ngoài những báo cáo cố định đã có |
| Quy trình hiện tại cần xác minh | 1. Người dùng xác định chỉ số cần xem · 2. Gửi yêu cầu cho người có quyền truy vấn · 3. Làm rõ điều kiện lọc · 4. Viết và chạy SQL · 5. Kiểm tra số liệu · 6. Trả kết quả |
| Bottleneck | Có thể nằm ở bước 2–4: chờ xử lý và làm rõ yêu cầu; **chưa đo trên quy trình khách hàng** |
| Impact | Người dùng phụ thuộc vào người kỹ thuật để lấy câu trả lời ngoài báo cáo có sẵn |
| Success metric | Baseline: [phút từ lúc yêu cầu đến khi có số liệu, số lần phải hỏi lại]; target đề xuất: giảm 50% thời gian với câu hỏi phù hợp, độ chính xác kết quả không thấp hơn truy vấn chuẩn; thử tối thiểu 20 câu hỏi |
| Phương án không dùng AI | Dashboard BI, báo cáo SQL định sẵn, bộ lọc và trình tạo báo cáo trực quan |
| Giả thuyết về AI | Mô hình local hiểu câu hỏi, lập truy vấn SQL chỉ đọc, giải thích kết quả và cho người dùng kiểm tra trước khi dùng ra quyết định |
| Cảm nhận nhanh | Workflow có bước AI; chưa chứng minh cần Agent |

```text
QUY TRÌNH HIỆN TẠI — cần xác nhận với khách
[1 Đặt câu hỏi: ?'] → [2 Gửi yêu cầu: ?']
→ [3 Làm rõ bộ lọc: ?'] → [4 Viết/chạy SQL: ?'] ← CẦN ĐO
→ [5 Kiểm tra số liệu: ?'] → [6 Trả kết quả: ?']
```

### Problem Card #2 — Chuyển câu hỏi thành SQL đúng với schema của khách

| Trường | Nội dung |
|---|---|
| Job Story | Khi người dùng hỏi bằng ngôn ngữ tự nhiên, tôi muốn hệ thống chọn đúng bảng, cột và quan hệ dữ liệu, để truy vấn trả đúng chỉ số mà họ hỏi. |
| Actor | Developer triển khai hệ thống Text-to-SQL và người dùng nghiệp vụ |
| Thời điểm / bối cảnh | Khi đưa một cơ sở dữ liệu mới vào hệ thống AI local hoặc khi người dùng đặt câu hỏi phức tạp |
| Quy trình hiện tại | 1. Kết nối schema · 2. Xác định bảng/cột liên quan · 3. Diễn giải câu hỏi · 4. Tạo SQL · 5. Kiểm tra quyền/cú pháp · 6. Chạy và đối chiếu kết quả |
| Bottleneck | Bước 2–4: ánh xạ ngôn ngữ nghiệp vụ sang cấu trúc bảng và điều kiện truy vấn; **cần đo bằng test case** |
| Impact | SQL có thể chạy thành công nhưng trả sai ý nghĩa, làm người dùng hiểu sai dữ liệu |
| Success metric | Baseline: [tỷ lệ kết quả đúng trên bộ test]; target đề xuất: tối thiểu 90% câu hỏi trong phạm vi demo khớp kết quả chuẩn; kiểm trên tối thiểu 30 câu hỏi có đáp án SQL tham chiếu |
| Phương án không dùng AI | Từ điển dữ liệu, các truy vấn SQL mẫu, giao diện chọn trường/điều kiện |
| Giả thuyết về AI | Chọn schema liên quan, sinh SQL và mô tả cách hiểu câu hỏi; validator và tài khoản DB chỉ đọc chặn truy vấn không hợp lệ |
| Cảm nhận nhanh | Workflow có AI kết hợp Rule kiểm tra cú pháp/quyền |

```text
LUỒNG XỬ LÝ TEXT-TO-SQL — bước cần đo chất lượng
[1 Nhận câu hỏi] → [2 Lấy schema liên quan]
→ [3 Xác định ý định/bộ lọc]  ← CẦN KIỂM THỬ
→ [4 Sinh SQL]  ← CẦN KIỂM THỬ
→ [5 Validate & giới hạn quyền] → [6 Thực thi/đối chiếu]
```

### Problem Card #3 — Kiểm chứng độ tin cậy của kết quả phân tích

| Trường | Nội dung |
|---|---|
| Job Story | Khi hỏi cùng một chỉ số theo các cách diễn đạt khác nhau, tôi muốn kết quả nhất quán và có căn cứ đối chiếu, để không quyết định dựa trên số liệu sai. |
| Actor | Người sử dụng báo cáo, developer và người kiểm tra số liệu |
| Thời điểm / bối cảnh | Khi nghiệm thu hoặc sử dụng Text-to-SQL cho các câu hỏi có điều kiện lọc và phép tổng hợp |
| Quy trình hiện tại | 1. Đặt câu hỏi · 2. Sinh SQL · 3. Xem câu SQL/điều kiện · 4. Chạy truy vấn · 5. Đối chiếu báo cáo chuẩn · 6. Ghi nhận câu hỏi sai |
| Bottleneck | Bước 3–5: kiểm tra tính đúng nghĩa của SQL và kết quả; **chưa có baseline** |
| Impact | Người dùng có thể nhận số liệu khác nhau hoặc thiếu căn cứ để tin tưởng kết quả |
| Success metric | Baseline: [tỷ lệ câu trả lời đúng, tỷ lệ nhất quán giữa các cách hỏi]; target đề xuất: 100% truy vấn được kiểm quyền, ít nhất 90% test case đúng và không có kết quả sai âm thầm trong tập kiểm thử |
| Phương án không dùng AI | Báo cáo chuẩn, bộ SQL đã kiểm thử, đối chiếu thủ công |
| Giả thuyết về AI | Hỗ trợ diễn đạt kết quả và cách hiểu câu hỏi; không tự khẳng định đúng khi không kiểm chứng được |
| Cảm nhận nhanh | Rule kiểm định kết quả + Workflow cho việc sinh SQL và xác nhận |

```text
KIỂM CHỨNG KẾT QUẢ — cần đo thời gian và độ chính xác
[1 Câu hỏi] → [2 Sinh SQL] → [3 Kiểm điều kiện]
→ [4 Chạy SQL] → [5 Đối chiếu truy vấn chuẩn] ← BƯỚC CẦN ĐO
→ [6 Ghi lỗi/cập nhật test case]
```

**Lưu ý về thời gian trong 3 quy trình CP2:** Ký hiệu `?'` thể hiện **chưa đo thực tế**, không phải 0 phút. Khi có log/ticket được phép sử dụng, ghi mốc bắt đầu/kết thúc từng bước để tính số phút; tránh tự gán số ước lượng thành quan sát. Bộ kiểm thử đối với card #2 và #3 có thể tạo từ schema và truy vấn mẫu đã được xác nhận, nhưng tỷ lệ 90% trong bảng hiện chỉ là **target đề xuất**.

### Card muốn pitch nhất

- **Card số:** 1 — Người dùng nghiệp vụ tự truy xuất số liệu từ cơ sở dữ liệu mà không cần viết SQL.
- **Vì sao:** Đây là mục tiêu có liên hệ rõ với dự án đã tham gia. Có thể kiểm chứng bằng câu hỏi thực tế của người dùng, thời gian chờ báo cáo và so sánh kết quả với SQL đúng.
- **Câu hỏi muốn nhóm phản biện:** Nếu một dashboard và vài bộ lọc đã đủ để người dùng lấy phần lớn số liệu, những loại câu hỏi nào vẫn buộc họ phải nhờ người biết SQL?

### AI đã phản biện card thế nào

| Điểm yếu AI chỉ ra | Đồng ý? | Đã sửa gì |
|---|---|---|
| Text-to-SQL là giải pháp, chưa phải bản thân problem | Đồng ý | Đặt problem ở nhu cầu tự tra cứu và phân tích dữ liệu của người nghiệp vụ |
| Chưa có bằng chứng người dùng phải chờ developer trả số liệu | Đồng ý | Giữ baseline cần xác minh, đề xuất hỏi về yêu cầu báo cáo gần nhất |
| SQL chạy được chưa chắc trả kết quả đúng | Đồng ý | Bổ sung metric độ chính xác so với truy vấn chuẩn và bước kiểm quyền |
| Dashboard có thể đủ dùng cho các chỉ số lặp lại | Đồng ý | Nêu phương án không AI, chỉ cân nhắc Text-to-SQL cho câu hỏi linh hoạt |

---
## 4. Tôi đã tham gia phần nào (CP3 → CP7)

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng tới bài nhóm |
|---|---|---|
| Pitch Problem Card | Chuẩn bị 3 card cá nhân về **Text-to-SQL**: người nghiệp vụ hỏi dữ liệu không cần SQL; ánh xạ ngôn ngữ tự nhiên vào schema; kiểm chứng kết quả truy vấn. Bảng CP3 của nhóm đã ghi 3 card #7–#9 dưới tên Bảo. | Đóng góp thêm một cluster riêng về truy vấn và kiểm chứng dữ liệu kinh doanh, để nhóm so sánh với AIOps và EdTech. |
| Phản biện bài của bạn khác | Theo bảng CP3 của nhóm, câu hỏi gắn tên Bảo gồm: số 90–120 phút là phát hiện hay điều tra; ngưỡng Confidence Score tính từ đâu; Rule thống kê có đủ lọc báo động giả không. Đây là các câu hỏi được bảng CP3 ghi nhận dưới tên tôi. | Làm rõ cách đo thời gian và an toàn khi để hệ thống tự can thiệp. |
| Nhận phản biện | Trong bảng pitch, card Text-to-SQL của mình được hỏi về khả năng Dashboard BI có sẵn, việc ánh xạ schema có phải problem kỹ thuật, và cách người không biết SQL kiểm tra kết quả. | Báo cáo nhóm nêu lý do không chọn Text-to-SQL: baseline phía khách chưa được đo và một phần nhu cầu có thể giải bằng BI. Đây là các điểm cần lưu ý để đánh giá lại phạm vi của đề tài. |
| Gom cluster / cây OST | Các card Text-to-SQL #7–#9 được ghi thành **Cluster C**. Mình được phân công hỗ trợ ghi bảng pitch, cluster và chấm điểm trong `TEAM.md`. | Bảng CP3 xếp nhóm AIOps 33/35, EdTech 31/35 và Text-to-SQL 27/35. Phần bảng tổng hợp được thể hiện trong báo cáo nhóm. |
| Chọn candidate problem | Đọc và đối chiếu shortlist CP3 trong báo cáo chung; nhóm chọn bài toán phản ứng sự cố ngoài giờ từ các nguồn log đa tầng thay cho Text-to-SQL. | Có một problem chung để phát triển quy trình và metric; việc chốt lựa chọn của cả nhóm được ghi trong `group_report.md`. |
| Kiểm chứng / research | Sử dụng bản tổng hợp CP4 đã được nhóm đưa vào repo để đối chiếu cách đặt problem, **không nhận là người trực tiếp phỏng vấn**. | Phát hiện khác biệt quan trọng: thời gian khoanh vùng thường được báo cáo là **15–30 phút**, không phải 90–120 phút như giả định đầu tiên; **2/5** người được hỏi thường bị gọi dậy ban đêm. |
| Quy trình nhóm | Dựa trên sơ đồ 6 bước và quy trình Rule–Agent–HITL–Rollback do Nguyên phụ trách để xác định đúng nơi viết bottleneck, metric và boundary. | Không nhầm thời gian khoanh vùng với thời gian từ bất thường đến cô lập; phân biệt hành động tự động với bước phải được người duyệt. |
| Problem Statement | Chuẩn bị nội dung v0 (CP5), v1 (CP6), bảng đối chiếu 8 thay đổi và 5 tiêu chí eval; gửi thay đổi vào **mục 5 và 7** của `report/team/group_report.md` qua PR #11 để nhóm review. | Đã có nội dung trong báo cáo nhóm về actor, workflow, bottleneck, baseline/target, boundary, điều kiện đánh giá; được gửi nhóm trưởng review trước khi chốt bản chung. |
| Mức can thiệp AI | Đối chiếu phần mình viết với phương án của nhóm ở mục 6: Rule lọc nhiễu, Agent chỉ đọc để điều tra, policy kiểm quyền và HITL/rollback. | Đặt yêu cầu 0 chặn nhầm, không sinh shell command và có bằng chứng log trước kết luận; mức can thiệp là **định hướng pilot**, chưa được kiểm chứng thực nghiệm. |
| Quyết định | Đọc định hướng **Go pilot có điều kiện tại Nginx** của nhóm và các tiêu chí kiểm tra an toàn; mục 8 do Hà Anh phụ trách. | Chưa nhận là người tự quyết Go/No-Go; kết luận cuối còn cần nhóm thống nhất. |

---

## 5. Dùng AI

| Checkpoint | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai hoặc hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| CP1 Scan | Trao đổi với ChatGPT để tìm hướng đề tài xuất phát từ trải nghiệm làm freelance và dự án Text-to-SQL đã triển khai. | Chuyển trọng tâm từ các pain chung như feedback Zalo sang câu hỏi dữ liệu tự nhiên dựa trên cơ sở dữ liệu khách hàng. | AI từng đề xuất đề tài kiểm tra chất lượng sản xuất dù mình không có trải nghiệm thực tế trong ngành này. | Mình đã phản đối việc gán trải nghiệm không có và yêu cầu dùng đúng dự án Text-to-SQL mình từng làm. |
| CP2 Problem Card | Nhờ AI hỗ trợ cấu trúc 3 Problem Cards về truy vấn nghiệp vụ, mapping schema và độ tin cậy kết quả. | Phân biệt pain của người dùng cuối với bài toán kỹ thuật bên trong Text-to-SQL; gợi ý các câu phản biện. | Có xu hướng suy diễn số phút chờ khách hoặc hiệu quả giải pháp khi chưa được đo. | Yêu cầu ghi thời gian/định lượng **chưa có baseline**, không tạo số liệu giả. |
| CP4 Research | Nhờ AI đối chiếu nội dung tổng hợp phỏng vấn đã có trong repo với giả định ban đầu của nhóm. | Chỉ ra kết quả **15–30 phút khoanh vùng** không thể dùng thay cho baseline **90–120 phút phát hiện→cô lập**. | Một số bản nháp ban đầu còn dùng số 90–120 như kết quả đã kiểm chứng hoặc gom các mốc thời gian khác nhau. | Dùng đúng thông tin trong báo cáo CP4; không trình bày mình là người trực tiếp phỏng vấn. |
| CP5 Quy trình | Nhờ AI đọc sơ đồ workflow đã có và đặt câu hỏi về bottleneck, quyền chỉ đọc, HITL và rollback. | Giúp phát hiện khác biệt giữa thời gian lọc log, chờ cảnh báo và thời gian xử lý ngoài giờ. | AI lúc đầu thêm một **phiếu đo** như thể đó là đầu việc chính của mình, trong khi phần thu thập số liệu thuộc CP4. | Mình đã hỏi lại và làm rõ phần được giao trong `TEAM.md` là **Problem Statement và Eval**, không phải tự phỏng vấn/điền phiếu đo. |
| CP5–6 Problem Statement | Dùng ChatGPT để phân tích cấu trúc v0/v1, tìm lỗ hổng metric/boundary, hỗ trợ chuẩn bị bản nháp trong file assets và mục 5, 7 của báo cáo nhóm. | Nêu rõ v0 là giả định, v1 cần dựa CP4; thêm điều kiện không chặn nhầm, không vượt quyền, phân biệt ngưỡng pilot và kết quả đo. | AI ban đầu nói đã “hoàn thiện” nhưng thực chất chỉ tạo file assets, còn `group_report.md` trống; nội dung sinh ra chưa phải câu chữ do mình tự chốt. | Mình đã chỉ ra phần v1 + eval vẫn trống và yêu cầu đưa tài liệu vào **đúng mục 5 và 7**; Bản cập nhật được gửi để nhóm review theo quy trình GitHub. |
| CP6 Mức can thiệp / quyết định | Nhờ AI kiểm tra cách diễn đạt Eval đối với phương án Rule + Bounded Agent + HITL nhóm dự kiến thử ở Nginx. | Gợi 5 tiêu chí: truy xuất được bằng chứng, khoanh vùng/không bỏ sót, cảnh báo giả, phân quyền/chặn nhầm và thời gian phản ứng. | Ngưỡng ≥85% confidence hoặc <5 phút không tự chứng minh tính an toàn; chưa có pilot và tập incident có nhãn để đối chiếu. | **Chưa xác nhận các ngưỡng này qua thử nghiệm**; sẽ chỉ ghi là target đề xuất và đưa cho nhóm duyệt, không báo là hệ thống đã đạt. |

---

## 6. Reflection (CP7)

**6.1. Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Từ bảng pitch CP3 của nhóm, tôi thấy ba nhóm vấn đề rất khác nhau: AIOps xử lý sự cố hạ tầng, EdTech kiểm tra câu hỏi hoặc bài tập, và Text-to-SQL để hỏi dữ liệu kinh doanh. Điều đáng chú ý là một vấn đề nghe có vẻ khó về công nghệ chưa chắc là vấn đề cần AI nhất. Chẳng hạn, việc thống kê các lỗi lặp lại trong bài Python có thể bắt đầu bằng linter hoặc unit test; việc xem số liệu kinh doanh cũng nên so với dashboard có sẵn. Với tôi, cách so sánh theo actor, bước nghẽn, bằng chứng và phương án không AI hữu ích hơn việc lựa chọn theo tên công nghệ.

**6.2. Nhóm có lúc nào bị “solution-first” không? Lúc đó nhóm nhận ra và xử lý thế nào?**

Trong tài liệu nhóm, candidate AIOps ban đầu gắn khá chặt với phương án Agentic AI và tự cô lập sự cố. Đây là chỗ cần cảnh giác với solution-first: câu hỏi đầu tiên phải là kỹ sư đang chậm ở bước nào, không phải triển khai Agent ra sao. Báo cáo nhóm sau đó tách ba opportunity: lọc cảnh báo giả, tra chéo log đa tầng và phản ứng ngoài giờ. Việc tách này giúp mô tả nhu cầu trước, rồi mới so sánh No AI, Rule, Workflow và Agent. Tuy vậy, tôi nghĩ nhóm vẫn phải chứng minh Agent vượt được Workflow trong pilot thay vì xem đó là điều hiển nhiên.

**6.3. Tôi có đổi ý sau khi bị phản biện không? Kể một lần cụ thể.**

Với hướng Text-to-SQL cá nhân, ban đầu tôi tập trung vào việc cho người dùng hỏi dữ liệu bằng ngôn ngữ tự nhiên. Khi xem lại các câu hỏi phản biện trong bảng CP3, tôi thấy cần tách vấn đề nghiệp vụ “người không biết SQL cần số liệu đúng lúc” khỏi vấn đề kỹ thuật “mô hình ánh xạ schema và JOIN”. Một dashboard hoặc công cụ BI có thể đã giải quyết phần nhu cầu tra cứu lặp lại. Vì vậy, đề xuất Text-to-SQL chỉ thuyết phục nếu xác định rõ những câu hỏi phát sinh ngoài báo cáo cố định, thời gian chờ thực tế và cách người dùng kiểm chứng kết quả. Đây là điều tôi rút ra từ quá trình chuẩn bị và xem lại các nhận xét trong báo cáo nhóm, không phải trích dẫn lời phát biểu ở buổi pitch.

**6.4. Kết quả kiểm chứng có làm tôi bất ngờ không? Điều gì?**

Điểm đáng chú ý nhất trong tổng hợp CP4 là thời gian khoanh vùng tầng lỗi phổ biến chỉ khoảng 15–30 phút, trong khi bản problem ban đầu dùng mốc 90–120 phút cho cả sự cố. Hai con số thực ra mô tả hai khoảng thời gian khác nhau. Ngoài ra, 2/5 người được hỏi thường bị gọi dậy giữa đêm; đa số không muốn hệ thống tự chặn vô điều kiện. Những dữ liệu này làm bài toán chuyển từ “đọc log nhanh hơn” sang “phát hiện và phản ứng ngoài giờ một cách an toàn”. Tôi không trực tiếp tham gia phỏng vấn; nhận xét này dựa trên bản tổng hợp mà nhóm đã ghi.

**6.5. Điều khó nhất khi viết Problem Statement là gì?**

Khó nhất là xác định metric không đánh tráo khái niệm. Thời gian từ lúc bất thường xuất hiện đến lúc có cảnh báo, thời gian kỹ sư tìm được tầng lỗi, và thời gian cô lập xong không giống nhau. Nếu dùng 15–30 phút khoanh vùng làm baseline rồi so với mục tiêu dưới 5 phút cô lập, kết quả sẽ thiếu công bằng. Tôi cũng phải phân biệt rõ điều đã có trong phỏng vấn với ngưỡng nhóm chỉ mới đề xuất, như confidence 85%, thời gian dưới 5 phút hay tỷ lệ cảnh báo sai dưới 15%. Problem Statement tốt không chỉ rõ pain mà còn nói rõ cách đo và việc hệ thống tuyệt đối không được tự làm.

**6.6. Nếu làm lại, tôi sẽ đổi gì? Tôi sẽ phản biện nhóm mạnh hơn ở điểm nào?**

Tôi sẽ yêu cầu nhóm thống nhất định nghĩa từng mốc thời gian ngay từ trước khi chấm điểm candidate: phát hiện, khoanh vùng, cô lập và khắc phục. Với Text-to-SQL, tôi sẽ chuẩn bị thêm bằng chứng từ câu hỏi nghiệp vụ thực tế và thử so sánh với dashboard BI để không lẫn vấn đề khách hàng với thử thách kỹ thuật của developer. Với AIOps, tôi muốn hỏi kỹ cách tính confidence score: điểm này đã được hiệu chuẩn trên incident có nhãn chưa, và tại sao 85% là ngưỡng đủ để chặn? Cuối cùng, tôi sẽ đề nghị kiểm thử trong môi trường mô phỏng, có whitelist, audit và rollback, trước khi cân nhắc bất kỳ hành động tự động nào trên production.

**6.7. Hiểu bài — chuỗi problem → quy trình → metric → boundary → mức can thiệp AI → quyết định**

Vấn đề nhóm chọn là việc phát hiện và phản ứng sự cố hạ tầng ngoài giờ bị chậm, kèm cảnh báo giả và việc phải đối chiếu nhiều nguồn log. Trong quy trình hiện tại, kỹ sư nhận cảnh báo, lọc log, tra chéo các tầng rồi mới quyết định cô lập hoặc chuyển người phụ trách. Các chỉ số cần đo riêng gồm thời gian phát hiện, thời gian khoanh vùng, thời gian cô lập, tỷ lệ cảnh báo giả và số lần chặn nhầm. Boundary là không tự chạy shell tùy ý, không tác động IP trong whitelist hoặc hệ thống lõi, và phải có người duyệt khi chứng cứ chưa đủ. Rule xử lý lọc nhiễu theo ngưỡng; Agent được nhóm đề xuất để chọn nguồn log cần đọc tiếp, còn quyền thực thi do policy và runbook có giới hạn kiểm soát. Nếu có tự cô lập ở tầng Nginx thì hành động phải có TTL, self-check, rollback và audit. Vì chưa có kết quả pilot đầy đủ, hướng Go có điều kiện của nhóm vẫn cần được xác nhận bằng thử nghiệm và tiêu chí dừng cụ thể.

---

## 7. Tài liệu tham khảo

- [Đề bài CHECKPOINTS](../../CHECKPOINTS.md)
- [Quy định sử dụng AI](../../RULES.md)
- [Rubric](../../RUBRIC.md)
- [Báo cáo nhóm HEHEHE — CP3–CP6](../team/group_report.md)
- [Tổng hợp phỏng vấn CP4 (nhóm thực hiện)](../assets/cp4-interview-tonghop.md)
- [Tài liệu quy trình CP5–CP6 của nhóm](../assets/2A202603937_cp5_cp6_workflow_and_ai_level.md)
