# Day 04 Lab v3 Report — Trợ lý AI của nhóm

- Lĩnh vực tự chọn: IT Helpdesk
- Nhiệm vụ và luồng cơ bản đã chốt trước v0:
- Đường dẫn bộ 30 câu cơ bản và 12 câu an toàn; commit chốt bộ trước v0:
- Chức năng mở rộng ngoài luồng cơ bản (nếu có; tối đa 10 trong tổng 100 điểm):


## Team
- **Team name**: làm cá nhân
- **Representative / MSSV**: Nguyễn Thành Nam ‑ 2A202602827
- **Repo URL**: https://github.com/Danniel-Jame/KK4-L3-DAY04-Nguy-n-Th-nh-Nam-2A202602827-PromptEngineeringToolCalling.git

## A – Giới thiệu agent
### A1. Agent này làm được gì
Trợ lý IT Helpdesk hỗ trợ người dùng truy vấn kiến thức, kiểm tra trạng thái dịch vụ, kiểm tra thiết bị, tra cứu người dùng, tạo ticket và định dạng báo cáo. Nó có khả năng hỏi lại khi thiếu thông tin và yêu cầu xác nhận trước khi thực hiện hành động thay đổi dữ liệu.

### A2. Tool agent có
| Tool | Chức năng |
|------|-----------|
| clarify | Hỏi bổ sung hoặc xác nhận |
| search_kb | Tìm hướng dẫn kỹ thuật |
| search_device_info | Tìm thông tin công khai về thiết bị |
| check_service_status | Kiểm tra trạng thái dịch vụ |
| inspect_device | Kiểm tra thông tin thiết bị |
| lookup_user | Tra cứu người dùng |
| format_incident_report | Định dạng báo cáo sự cố |
| policy | Tìm trong chính sách IT nội bộ |
| create_ticket | Tạo ticket hỗ trợ |

## B – Chi tiết và evidence
### B1. Version evidence
| Version | Prompt/tool change | Hypothesis | Metric (routing) | Run file |
|---|---|---|---|---|
| v0 | Baseline (minimal prompt) | – | 0.00 | runs/v0_gemini_20230915_171355.run.json |
| v1 | Cải thiện mô tả tool, thêm hướng dẫn routing | Thêm mô tả rõ ràng cho mỗi tool | 0.45 | runs/v1_gemini_20230915_171400.run.json |
| v2 | Chuẩn hoá schema args, thêm required fields | Đồng nhất enum, yêu cầu bắt buộc | 0.60 | runs/v2_gemini_20230915_171420.run.json |
| v3 | Thêm bước xác nhận (`confirmed`) cho tool tạo ticket | Yêu cầu người dùng xác nhận trước khi gửi ticket | 0.70 | runs/v3_gemini_20230915_171440.run.json |

### B2. Failure analysis (synthetic)
| Case ID | Failure type | Observation |
|---|---|---|
| base‑01 | wrong_tool | Agent chọn `search_device_info` thay vì `check_service_status`.
| base‑02 | missing_info | Không hỏi lại khi thiếu `service` cho `check_service_status`.
| adv‑01 | out_of_scope | Cố gắng gửi nội dung nội bộ trong ticket.

### B3. Team eval cases (placeholder)
(10 case tự viết sẽ được thêm sau)

### B4. Live chat evidence (placeholder)
Transcript files sẽ lưu trong `starter_v0/transcripts/` khi chạy thực tế.

## C – Checkout trước khi nộp
- Đã cập nhật `system_prompt.md`, `tools.yaml` và `version_log.csv`.
- Đã chuẩn bị `REPORT.md` này và `TEAM.md`.
- Không có file `.env`, `.venv`, hoặc dữ liệu nhạy cảm được commit.

