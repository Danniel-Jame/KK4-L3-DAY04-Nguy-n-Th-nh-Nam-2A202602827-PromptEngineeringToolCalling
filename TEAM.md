# TEAM — Day04, K4-L3B

**Làm cá nhân.** Người làm tự viết và commit phần INDIVIDUAL của mình.

## Thông tin bài nộp

- Tên nhóm: làm theo cá nhân
- Người đại diện / MSSV: Nguyễn Thành Nam — 2A202602827
- Tên repo: `KK4-L3-DAY04-Nguy-n-Th-nh-Nam-2A202602827-PromptEngineeringToolCalling`
- URL repo, nhánh nộp, commit chốt: https://github.com/nguyenthanhnam/KK4-L3-DAY04-Nguy-n-Th-nh-Nam-2A202602827-PromptEngineeringToolCalling — nhánh `main` — commit `complete`


## Thành viên

| Họ và tên          | MSSV         | GitHub            | Vai trò và công việc                                      | File/commit/PR                          |
|--------------------|--------------|-------------------|-----------------------------------------------------------|-----------------------------------------|
| Nguyễn Thành Nam   | 2A202602827  | nguyenthanhnam    | Làm toàn bộ bài (prompt, tool, eval, UI, report)         | Toàn bộ file trong repo, commit trên main |

## Nhận xét chung

- Kết quả và bằng chứng: Đã chạy đầy đủ v0 → v3 trên cùng bộ case, lưu run JSON, `version_log.csv`, transcript và `REPORT.md`. Agent chọn tool đúng hơn, xử lý multi-turn và an toàn dữ liệu tốt hơn so với baseline.
- Thay đổi hiệu quả nhất: Cải thiện `system_prompt.md` (rõ ràng hơn về khi nào hỏi lại / khi nào gọi tool) và mô tả tool trong `tools.yaml` giúp giảm sai tool & sai input.
- Giới hạn còn lại: Một số case multi-turn phức tạp và adversarial vẫn còn lỗi; UI còn cơ bản; chưa có chức năng mở rộng ngoài luồng chính.
- Cách phân công và tích hợp: Làm cá nhân, không phân công nhóm. Tự thực hiện toàn bộ quy trình từ baseline đến báo cáo.

## INDIVIDUAL

### Nguyễn Thành Nam — 2A202602827

- Phần việc và file/commit/PR:
  - Cải thiện `artifacts/system_prompt.md` và `artifacts/tools.yaml`
  - Chạy và lưu kết quả v0, v1, v2, v3
  - Viết `data/eval_group.json` (5 one-turn + 5 multi-turn)
  - Chạy adversarial/safety và phân tích
  - Xây UI chat hiển thị tool call / input / kết quả / version
  - Viết `artifacts/REPORT.md` và hoàn thiện `TEAM.md`
  - Commit toàn bộ trên nhánh `main`

- Quyết định, khó khăn và cách xử lý:
  - Quyết định giữ lĩnh vực IT Helpdesk (dùng bộ case có sẵn) thay vì đổi đề tài để tập trung vào prompt/tool engineering.
  - Khó khăn: Agent hay chọn sai tool hoặc điền thiếu tham số ở multi-turn. Xử lý bằng cách thêm quy tắc rõ ràng trong system prompt và mô tả tool chi tiết hơn, sau đó so sánh metric trước/sau từng phiên bản.

- Điều đã học:
  - Cách viết system prompt và tool declaration ảnh hưởng rất lớn đến hành vi agent.
  - Cần eval có cấu trúc (base + multi-turn + adversarial) và so sánh version mới thấy được tiến bộ thực sự.
  - Luôn kiểm tra tool result/error, không chỉ dựa vào routing PASS.

- AI/công cụ đã dùng và cách kiểm tra:
  - Dùng AI hỗ trợ viết/sửa prompt và phân tích lỗi từ transcript.
  - Kiểm tra bằng cách chạy lại toàn bộ eval suite sau mỗi thay đổi, đối chiếu metric và đọc từng tool call/result.
