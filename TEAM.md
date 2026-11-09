# Team

## Thông tin nhóm

- Tên nhóm: HEHEHE
- Candidate problem nhóm chọn (1 câu): Kỹ sư trực ca vận hành mất 90-120 phút mỗi sự cố để lần mò thủ công qua hàng chục nguồn log rời rạc và thiếu cơ chế AI tự chủ có kiểm soát (Agentic AI phân quyền theo cột mốc `Confidence Score` kết hợp `HITL`) để vừa cô lập tức thì bất thường rõ bằng chứng vào ban đêm vừa giữ lại ca nhạy cảm chờ con người duyệt.
- Quyết định cuối (Go / Not Yet / No-Go): **Go — pilot có điều kiện** tại tầng Nginx, bắt đầu bằng shadow/read-only và chỉ mở auto-containment cục bộ sau khi đạt các cổng an toàn.

## Thành viên

| STT | Họ và tên | MSSV | Vai trò trong nhóm | Tài khoản GitHub |
|---:|---|---|---|---|
| 1 | Bùi Đặng Nhật Nguyên | 2A202603937 | Owner problem, Domain expert - vẽ quy trình, thiết kế khung quản trị Agentic AI (`Confidence Score` + `HITL`), AI Canvas, so sánh 4 mức AI | double-n-021 |
| 2 | Đỗ Hoàng Vũ | 2A202603920 | Kiểm chứng (phỏng vấn), điều phối, quản trị repo | hoangvu1806 |
| 3 | Trần Gia Bảo | 2A202603914 | Người viết — Problem Statement v0 và v1, 3–5 tiêu chí đánh giá | *(tự cập nhật)* |
| 4 | Trần Thị Hà Anh | 2A202603887 | Research + Quyết định — bảng công cụ có link, 4 rủi ro, ngưỡng dừng | hnha02 |

Không ghi email hay số điện thoại vào bảng này, vì repo có thể để public.

## Phân công theo checkpoint

| Checkpoint | Người chính | Người hỗ trợ | Sản phẩm |
|---|---|---|---|
| CP3 — Hội tụ nhóm | Nguyên (dẫn pitch) | Bảo (ghi bảng pitch, cluster, chấm điểm) | Bảng pitch 12 card, cluster, cây OST, bảng chấm điểm 7 tiêu chí, lý do loại ≥2 candidate |
| CP4 — Kiểm chứng | Vũ | Nguyên (câu hỏi domain) | Assumption Map 4–6 giả định, 3 Interview Snapshot trong `report/assets/cp4-interview-snapshot-{1,2,3}.md`, câu "nhóm đã sửa problem thế nào" |
| CP4 — Research | Hà Anh | Nguyên | Bảng research 3 công cụ (Datadog Watchdog, Dynatrace Davis AI, PagerDuty AIOps) có link đã mở và kiểm |
| CP5 — Quy trình trước/sau | Nguyên | Vũ (review thời gian) | Mermaid quy trình hiện tại 6 bước + quy trình tương lai có Agent + HITL + Rollback, bảng before/after |
| CP5 — Problem Statement v0 | Bảo | Nguyên (xác nhận domain), Vũ (phản biện) | PS v0 đủ 6 trường: Actor, Quy trình, Bottleneck, Impact, Success Metric có baseline→target và cách đo, Boundary |
| CP6 — Mức can thiệp + Problem Statement v1 | Nguyên (ma trận, 4 mức, AI Canvas, PAIR), Bảo (v1 + eval) | Hà Anh (phản biện) | Ma trận mơ hồ×phức tạp, bảng so sánh 4 mức với lý do không chọn Workflow, AI Canvas, 2 câu PAIR, 3–5 tiêu chí đánh giá, PS v1 + bảng thay đổi v0→v1 |
| CP6 — Quyết định | Hà Anh | Cả nhóm | Bảng 4 rủi ro Value/Usability/Feasibility/Viability có lý do, quyết định Go/Not Yet/No-Go, ngưỡng dừng đo được |

## Timeline

| Giai đoạn | Thời gian | Việc |
|---|---|---|
| **G0 — Chuẩn bị** | 2–3 ngày trước buổi họp | Vũ chạy 3 phỏng vấn + viết snapshot; Hà Anh đọc 3 trang research + draft bảng; Nguyên vẽ draft 2 sơ đồ Mermaid; Bảo tạo nhánh `team-cp3-cp6` + dán khung |
| **G1 — Họp** | 130 phút trong buổi lab | CP3 (30'), CP4 (30'), CP5 (45'), CP6 (25') |
| **G2 — Hoàn thiện** | 1–2 ngày sau buổi họp | Bảo chốt PS v1 + eval; Hà Anh viết ngưỡng dừng; cả 4 cập nhật mục 4, 5, 6 trong báo cáo cá nhân; điền phần cá nhân trong `TEAM.md`; mở PR team-cp3-cp6 → main |
| **G3 — Nộp** | Trước deadline | Mỗi người nộp link repo lên LMS bằng tài khoản mình |

## Luật áp dụng

- CP3 pitch + phản biện: **không AI**.
- CP4 phỏng vấn: **không AI đóng vai người dùng**. Không phỏng vấn thành viên nhóm mình. Bịa kết quả → C7 = 0 cho cả nhóm.
- CP5–CP6: AI chỉ dùng để phản biện v0, v1, mức can thiệp. Prompt "chỉ ra lỗ hổng, không viết lại thay".
- Mỗi lần dùng AI → ghi vào bảng mục 5 của báo cáo cá nhân.
- Mỗi người commit phần của mình bằng tài khoản GitHub của chính mình.

## Cá nhân

Mỗi thành viên tự điền mục của mình.

### Bùi Đặng Nhật Nguyên - 2A202603937

**Phần việc phụ trách:**

- Owner problem, domain expert vận hành hạ tầng và log đa tầng
- CP3 dẫn pitch bài toán giám sát đa nguồn log và thiết kế Agentic AI có kiểm soát (`Bounded Autonomy`)
- CP5 vẽ quy trình hiện tại (6 bước thủ công) và quy trình tương lai (Mermaid: `Rule` lọc nhiễu -> `Agent` tự chủ điều tra -> phân nhánh theo `Confidence Score` và `HITL` -> `Self-Check & Rollback`), bảng so sánh Before/After
- CP6 lập ma trận mơ hồ x phức tạp, bảng so sánh 4 mức AI (lập luận vì sao `Workflow` không đủ), AI Canvas, trả lời 2 câu hỏi Google PAIR

**Đóng góp cụ thể** (mình đã làm gì, ra sản phẩm gì):

- Hoàn thành báo cáo cá nhân CP1 (8 vấn đề vận hành log đa tầng) và CP2 (3 Problem Cards kết nối thành vòng khép kín: màng lọc nhiễu chu kỳ, Agent tự chủ theo `Confidence Score`, và nhánh bàn giao bằng chứng `HITL`).
- Xây dựng mục 4 (Quy trình trước/sau CP5) và mục 6 (Mức can thiệp AI CP6) trong báo cáo nhóm kèm tài liệu phân tích chi tiết: thiết kế cơ chế phân quyền 3 cột mốc `Confidence Score` (`< 60%` theo dõi, `60% - < 85%` chuyển `HITL`, `>= 85%` tự thực thi kịch bản cục bộ an toàn kèm nút Hoàn tác 1 chạm) và giải đáp các câu hỏi chuyên môn hạ tầng cho nhóm.

**Bằng chứng** (phần nào trong `group_report.md`, file nào trong `report/assets/`, commit nào):

- Báo cáo cá nhân: `report/individual/2A202603937_BuiDangNhatNguyen.md` (commit `ae0c87c`, `2659d78`).
- Báo cáo nhóm: Mục 1, Mục 2 (`2.1 -> 2.4` - CP3), Mục 3 (`3.3 Research` - CP4), Mục 4 (`4.1 -> 4.3` - CP5) và Mục 6 (`6.1 -> 6.4` - CP6) trong `report/team/group_report.md`.
- Tài liệu thiết kế chuyên môn và hỗ trợ câu hỏi phỏng vấn domain: `report/assets/2A202603937_cp5_cp6_workflow_and_ai_level.md`, `report/assets/cp4-cauhoi-phongvan.md`.

**Điều mình học được từ phần nhóm:**

- Khi chuyển từ ý tưởng cá nhân sang bài toán nhóm, mình nhận ra muốn đưa Agentic AI vào vận hành hạ tầng thực tế thì không thể chỉ nói "cho AI tự chặn", mà phải định nghĩa rõ ranh giới tự chủ (`Bounded Autonomy`): tách bạch thời gian phát hiện trễ với thời gian điều tra, tính `Confidence Score` từ tín hiệu kỹ thuật độc lập thay vì để LLM tự đoán, khóa hành động trong kịch bản tham số hóa có sẵn (Parameterized Runbook) và luôn giữ chốt chặn `HITL` cho các dịch vụ cốt lõi.

### Đỗ Hoàng Vũ — 2A202603920

**Phần việc phụ trách:**

- Điều phối thời gian, quản trị repo (fork, mời collaborator, merge PR)
- CP4 kiểm chứng: phỏng vấn 2–3 kỹ sư DevOps/SRE, viết Interview Snapshot
- CP4 Assumption Map
- Mục 9 (Hạn chế) và mục 10 (Tài liệu tham khảo) của báo cáo nhóm

**Đóng góp cụ thể** (mình đã làm gì, ra sản phẩm gì):

- Soạn bộ câu hỏi phỏng vấn theo The Mom Test cho đề log đa nguồn
- Phỏng vấn 5 người ngoài nhóm (DevOps/SRE, quản trị hệ thống, dev backend) qua gặp trực tiếp, gọi điện và nhắn tin; tổng hợp kết quả
- Viết Assumption Map 6 giả định, bảng tín hiệu xác nhận / phản bác, và 3 điểm nhóm sửa problem sau kiểm chứng (baseline 15–30 phút, trọng tâm sự cố ngoài giờ, siết boundary)
- Lập bảng phân công và timeline CP3–CP6 trong `TEAM.md`
- Quản trị repo: chia nhánh, review và merge PR, kiểm tra conflict giữa các PR
- Viết mục 9 và mục 10 của báo cáo nhóm

**Bằng chứng** (phần nào trong `group_report.md`, file nào trong `report/assets/`, commit nào):

- `group_report.md` mục 3.1, 3.2, 9, 10
- `report/assets/cp4-cauhoi-phongvan.md`, `report/assets/cp4-interview-tonghop.md`
- Commit `29eb7e3` (CP4, PR #8), `2798a48` (phân công trong `TEAM.md`, PR #6), `4294c15` (báo cáo cá nhân, PR #2)

**Điều mình học được từ phần nhóm:**

- Hỏi về hành vi đã xảy ra ("lần sự cố gần nhất mất bao lâu") cho ra số liệu khác hẳn con số ước lượng trong card: 15–30 phút thay vì 60–90 phút
- Người dùng không từ chối tự động hóa, nhưng chỉ chấp nhận khi có ràng buộc rõ: whitelist, rollback và giới hạn thời gian

### Trần Gia Bảo — 2A202603914

**Phần việc phụ trách:**

- Người phụ trách nội dung Problem Statement v0 (CP5), Problem Statement v1 (CP6), bảng thay đổi và 3–5 tiêu chí đánh giá (eval).
- Chuẩn bị 3 Problem Cards cá nhân về Text-to-SQL để nhóm đưa vào bảng pitch, cluster và shortlist ở CP3.

**Đóng góp cụ thể** (đã có sản phẩm lưu trên repo):

- Hoàn thành báo cáo cá nhân CP1 (8 problem) và CP2 (3 Problem Cards về truy xuất dữ liệu nghiệp vụ, chuyển ngôn ngữ tự nhiên thành SQL và kiểm chứng kết quả).
- Bổ sung nội dung mục 5 `Problem Statement v0` của báo cáo nhóm với 6 trường Actor, Quy trình, Bottleneck, Impact, Success Metric và Boundary.
- Bổ sung mục 7 `Problem Statement v1 + tiêu chí đánh giá`: 9 trường nội dung, bảng đối chiếu v0 → v1 có lý do và 5 tiêu chí eval (bằng chứng truy xuất, khoanh vùng đúng, lọc cảnh báo giả, an toàn phân quyền, thời gian phản ứng).
- Đối chiếu kết quả tổng hợp CP4 để phân biệt thời gian **khoanh vùng tầng lỗi 15–30 phút** với giả định ban đầu **90–120 phút từ khi có bất thường đến lúc cô lập**, tránh dùng hai chỉ số khác định nghĩa làm baseline và target.
- Gửi các thay đổi lên nhánh `TranGiaBao` và mở PR để nhóm trưởng review; không nhận là người trực tiếp phỏng vấn CP4 hay người quyết định cuối CP6.

**Bằng chứng** (đường dẫn trong repo và commit):

- `report/individual/2A202603914_TranGiaBao.md` — CP1, CP2 và mục 4–6 báo cáo cá nhân.
- `report/team/group_report.md` — mục **2.1** (candidate #7–#9 của Bảo), **2.2** (Cluster C — Text-to-SQL), **5** (Problem Statement v0), **7** (Problem Statement v1, thay đổi v0→v1, 5 eval).
- `report/assets/2A202603914_cp5_cp6_deliverables.md` và `report/assets/2A202603914_cp5_cp6_review_notes.md` — phân tích và ghi chú phục vụ review.
- GitHub commit [`48a69f0`](https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming/commit/48a69f097c2afe119c63c45ca5046d30d81aad93) và [PR #11](https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming/pull/11): cập nhật trực tiếp mục 5, 7 báo cáo nhóm.
- GitHub commit [`f18ae11`](https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming/commit/f18ae11cc3fa5a896a865c165d73f34bbfde2bc6) và [PR #12](https://github.com/hoangvu1806/K5-L3B-DAY02-HEHEHE-DiscoveryProblemFraming/pull/12): cập nhật bài cá nhân.

**Bài học chuyên môn từ phần được giao:**

- Khi xây dựng Problem Statement, phải phân biệt **thời gian phát hiện**, **thời gian khoanh vùng** và **thời gian cô lập**; baseline và target chỉ so sánh được khi đo cùng một mốc.
- Metric tốc độ phải đi kèm metric chất lượng và an toàn. Với đề tài này, phản ứng nhanh nhưng chặn nhầm người dùng hợp lệ không thể xem là thành công.
- Cần thử phương án `No AI / Rule / Workflow` trước khi nâng lên Agent; trong phương án Agent có kiểm soát, quyền thực thi phải tách khỏi suy luận ngôn ngữ và luôn có `HITL`, `whitelist`, `rollback`.

### Trần Thị Hà Anh — 2A202603887

**Phần việc phụ trách:**

- CP4 research: bảng 3 công cụ (Datadog Watchdog, Dynatrace Davis AI, PagerDuty AIOps) có link đã mở và kiểm
- CP6 bảng 4 rủi ro Value/Usability/Feasibility/Viability
- CP6 quyết định Go/Not Yet/No-Go và ngưỡng dừng đo được

**Đóng góp cụ thể** (mình đã làm gì, ra sản phẩm gì):

- Hoàn thành CP1 với 8 Job Story và CP2 với 3 Problem Card cho scenario giáo viên dạy lập trình; pitch 3 candidate #10–#12 để nhóm so sánh với AIOps và Text-to-SQL.
- Kiểm tra tài liệu chính thức của Datadog Watchdog, Dynatrace Davis AI và PagerDuty AIOps/Event Orchestration; sửa bảng research để tách rõ anomaly/RCA, event orchestration và quyền thực thi, đồng thời bỏ các khẳng định chi phí/bảo mật chưa có nguồn.
- Đánh giá 4 rủi ro Value/Usability/Feasibility/Viability dựa trên tổng hợp 5 phỏng vấn; chốt **Go — pilot có điều kiện** theo hai giai đoạn shadow/read-only và auto-containment cục bộ.
- Viết tiêu chí mở quyền và ngưỡng dừng đo được: dừng ngay khi có vi phạm quyền/whitelist, rollback thất bại hoặc bỏ sót sự cố nghiêm trọng; nếu không đạt chất lượng thì quay về Rule + Workflow read-only + HITL.

**Bằng chứng** (phần nào trong `group_report.md`, file nào trong `report/assets/`, commit nào):

- Báo cáo cá nhân: `report/individual/2A202603887_TranThiHaAnh.md` (CP1–CP2 ở commit `3edf93a`; nhật ký CP3–CP6, bảng dùng AI và phần việc nhóm ở commit `aaab6fb`; CP7 ở commit `ff7cdf0`).
- Báo cáo nhóm: mục `3.3 Research giải pháp đã có`, mục `8.1 Bốn rủi ro`, mục `8.2 Kết luận`, mục `9 Hạn chế` và mục `10 Tài liệu tham khảo` trong `report/team/group_report.md`.
- Bằng chứng kiểm chứng dùng để ra quyết định: `report/assets/cp4-interview-tonghop.md`.

**Điều mình học được từ phần nhóm:**

- Research không chỉ để liệt kê công cụ mà phải chỉ ra công cụ giải đúng bước nào, cần dữ liệu gì và còn thiếu gì so với bài toán. Kết quả phỏng vấn cho thấy pain ngoài giờ là thật, đủ để nhóm **Go cho một pilot nhỏ và có thể đảo ngược**, nhưng baseline 90–120 phút và các ngưỡng 60/85 chưa được log xác nhận. Vì vậy nhóm tách Agent đọc/đề xuất khỏi policy cấp quyền, bắt đầu bằng shadow mode và chỉ mở auto-containment sau khi đạt cổng an toàn.
