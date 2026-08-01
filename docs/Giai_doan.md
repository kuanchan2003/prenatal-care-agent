# KẾ HOẠCH HOÀN THÀNH MVP TRONG 2 TUẦN

## 1. Mục tiêu cuối cùng của dự án

Sau hai tuần, nhóm cần hoàn thành một ứng dụng web **AI Agent Trợ Lý Tiền Sản** có hai vai trò:

### Thai phụ

* Đăng nhập.
* Tạo hồ sơ thai kỳ.
* Nhập ngày dự sinh.
* Xem tuần thai và tam cá nguyệt.
* Xem timeline các mốc khám, xét nghiệm, siêu âm và tiêm chủng.
* Xem reminder trong ứng dụng.
* Hỏi đáp kiến thức thai kỳ có nguồn.
* Khai báo triệu chứng.
* Nhận cảnh báo khi có dấu hiệu nguy hiểm.
* Ghi cân nặng và huyết áp.

### Bác sĩ

* Đăng nhập.
* Xem danh sách thai phụ.
* Xem hồ sơ và timeline của thai phụ.
* Xem nhật ký cân nặng và huyết áp.
* Xem cảnh báo dấu hiệu nguy hiểm.
* Đánh dấu cảnh báo đã xem hoặc đã xử lý.
* Cập nhật ngày dự sinh.
* Xem timeline được tính lại.

### AI Agent

* Nhận câu hỏi của người dùng.
* Tải thông tin thai kỳ.
* Xác định loại yêu cầu.
* Gọi đúng công cụ.
* Truy xuất tài liệu khi hỏi kiến thức.
* Kiểm tra dấu hiệu nguy hiểm trước khi trả lời.
* Không chẩn đoán và không tư vấn thuốc.
* Trả lời có nguồn và disclaimer.

---

# 2. Tổng quan các giai đoạn

| Giai đoạn   |  Thời gian | Kết quả chính                                            |
| ----------- | ---------: | -------------------------------------------------------- |
| Giai đoạn 1 |   Ngày 1–2 | Chốt yêu cầu, kiến trúc, database, API và bộ khung dự án |
| Giai đoạn 2 |   Ngày 3–4 | Xây hồ sơ thai kỳ, tính tuần thai và timeline            |
| Giai đoạn 3 |   Ngày 5–6 | Xây RAG và AI Agent hỏi đáp có nguồn                     |
| Giai đoạn 4 |   Ngày 7–8 | Xây sàng lọc triệu chứng, red-flag và doctor alert       |
| Giai đoạn 5 |  Ngày 9–10 | Xây nhật ký sức khỏe, doctor dashboard và tích hợp       |
| Giai đoạn 6 | Ngày 11–14 | Kiểm thử, sửa lỗi, deploy và chuẩn bị demo               |

---

# GIAI ĐOẠN 1 — PHÂN TÍCH, THIẾT KẾ VÀ KHỞI TẠO DỰ ÁN

## Thời gian

Ngày 1 đến ngày 2.

## Mục tiêu

Tạo nền móng chung để tất cả thành viên phát triển cùng một kiến trúc, cùng tên dữ liệu, cùng API và không làm lệch phạm vi MVP.

Giai đoạn này chưa cần xây tính năng hoàn chỉnh.

---

## Yêu cầu cần đạt

Nhóm phải thống nhất:

* Phạm vi MVP.
* Những chức năng không làm.
* Hai vai trò `PATIENT` và `DOCTOR`.
* Ba kịch bản demo.
* Kiến trúc tổng thể.
* Cấu trúc repository.
* Database schema.
* API contract.
* Luồng AI Agent.
* Thiết kế RAG.
* Timeline rules ban đầu.
* Red-flag rules ban đầu.
* Wireframe các màn hình.
* Quy trình Git.

---

## Những việc cần làm

### 1. Chốt phạm vi MVP

Các chức năng bắt buộc:

* Đăng nhập.
* Hồ sơ thai kỳ.
* Tuần thai.
* Timeline.
* Reminder trong ứng dụng.
* Chat RAG.
* Citation.
* Symptom screening.
* Red-flag alert.
* Nhật ký cân nặng.
* Nhật ký huyết áp.
* Doctor dashboard.
* Cập nhật ngày dự sinh.

Các chức năng không làm:

* Mobile app.
* Push notification.
* Kết nối thiết bị y tế.
* Chẩn đoán.
* Kê thuốc.
* Phân tích xét nghiệm.
* Đọc ảnh siêu âm.
* Multi-agent.
* Fine-tuning.
* Dữ liệu bệnh nhân thật.

### 2. Xây ba kịch bản demo

#### Kịch bản 1: Theo dõi thai kỳ

```text
Đăng nhập
→ tạo hồ sơ
→ nhập ngày dự sinh
→ tính tuần thai
→ tạo timeline
→ xem mốc tiếp theo
→ hỏi AI
→ nhận câu trả lời có nguồn
```

#### Kịch bản 2: Dấu hiệu nguy hiểm

```text
Nhập triệu chứng
→ rule engine kiểm tra
→ phát hiện red flag
→ hiển thị cảnh báo
→ tạo doctor alert
→ bác sĩ đánh dấu đã xử lý
```

#### Kịch bản 3: Thay đổi ngày dự sinh

```text
Bác sĩ cập nhật ngày dự sinh
→ lưu lịch sử thay đổi
→ tính lại tuần thai
→ cập nhật các mốc tương lai
→ thai phụ xem timeline mới
```

### 3. Khởi tạo repository

Cấu trúc dự kiến:

```text
prenatal-care-agent/
├── backend/
├── frontend/
├── docs/
├── seed/
├── eval/
├── scripts/
├── infrastructure/
├── docker-compose.yml
├── .env.example
└── README.md
```

### 4. Khởi tạo backend

* Tạo FastAPI project.
* Tạo endpoint `/health`.
* Tạo Swagger.
* Tạo PostgreSQL bằng Docker.
* Chuẩn bị pgvector.
* Tạo cấu hình environment.

### 5. Khởi tạo frontend

* Tạo Next.js.
* Sử dụng TypeScript.
* Sử dụng Tailwind CSS.
* Tạo route khung cho patient và doctor.
* Tạo layout chung.

### 6. Thiết kế database

Các bảng tối thiểu:

```text
users
pregnancies
doctor_patient_assignments
pregnancy_due_date_history
timeline_rules
pregnancy_milestones
reminders
weight_entries
blood_pressure_entries
symptom_entries
danger_sign_rules
danger_sign_events
clinician_alerts
knowledge_documents
knowledge_chunks
conversations
conversation_messages
audit_logs
```

### 7. Viết API contract

Phải định nghĩa trước:

```text
POST   /auth/login
GET    /auth/me

POST   /pregnancies
GET    /pregnancies/me
PATCH  /pregnancies/{id}/due-date

GET    /pregnancies/{id}/dashboard
GET    /pregnancies/{id}/timeline

POST   /chat
GET    /chat/history

POST   /symptoms/screen

POST   /journal/weight
POST   /journal/blood-pressure

GET    /doctor/patients
GET    /doctor/patients/{id}
GET    /doctor/alerts
PATCH  /doctor/alerts/{id}/acknowledge
```

### 8. Chuẩn bị rules

* 10–15 timeline rules.
* 10–15 red-flag rules.
* Disclaimer.
* Template cảnh báo cố định.
* 10–20 safety test cases.

### 9. Thiết kế Agent

Agent tối giản:

```text
START
→ Load Pregnancy Context
→ Safety Check
→ Intent Router
→ Tool hoặc RAG
→ Output Guardrail
→ Save Conversation
→ END
```

---

## Kết quả cần đạt

* FastAPI chạy được.
* Next.js chạy được.
* PostgreSQL chạy được.
* Có Swagger.
* Có database schema.
* Có API contract.
* Có Agent flow.
* Có RAG design.
* Có wireframe.
* Có timeline rules.
* Có danger-sign rules.
* Có Master Context Prompt.
* Tất cả thành viên dùng chung kiến trúc.

---

# GIAI ĐOẠN 2 — HỒ SƠ THAI KỲ, TUẦN THAI VÀ TIMELINE

## Thời gian

Ngày 3 đến ngày 4.

## Mục tiêu

Hoàn thành luồng cơ bản đầu tiên:

```text
Thai phụ đăng nhập
→ tạo hồ sơ thai kỳ
→ nhập ngày dự sinh
→ hệ thống tính tuần thai
→ tạo timeline
→ hiển thị mốc tiếp theo
```

---

## Yêu cầu cần đạt

Hệ thống phải:

* Tạo được hồ sơ thai kỳ.
* Tính được tuần thai.
* Xác định tam cá nguyệt.
* Tạo milestone từ timeline rules.
* Hiển thị mốc tiếp theo.
* Không tạo milestone trùng.
* Cho phép bác sĩ đổi ngày dự sinh.
* Lưu lịch sử thay đổi ngày dự sinh.
* Chỉ cập nhật milestone tương lai chưa hoàn thành.

---

## Những việc cần làm

### 1. Xây authentication cơ bản

* Tạo tài khoản demo.
* Đăng nhập bằng email và mật khẩu.
* Trả về access token.
* Phân biệt `PATIENT` và `DOCTOR`.
* Kiểm tra quyền ở backend.

### 2. Xây pregnancy profile

Các trường chính:

```text
id
patient_id
estimated_due_date
pregnancy_type
status
created_at
updated_at
```

MVP có thể mặc định:

```text
pregnancy_type = singleton
status = active
```

### 3. Viết hàm tính tuần thai

Cách tính đơn giản:

```text
Ngày bắt đầu thai kỳ ước tính = ngày dự sinh - 280 ngày

Số ngày thai = ngày hiện tại - ngày bắt đầu thai kỳ

Tuần thai = số ngày thai / 7
```

Cần xử lý:

* Due date không hợp lệ.
* Ngày dự sinh quá xa.
* Tuần thai nhỏ hơn 0.
* Tuần thai lớn hơn giới hạn hợp lý.

### 4. Xác định tam cá nguyệt

Có thể dùng logic MVP:

```text
Tuần 1–13: tam cá nguyệt 1
Tuần 14–27: tam cá nguyệt 2
Tuần 28 trở đi: tam cá nguyệt 3
```

### 5. Tạo timeline service

Input:

```json
{
  "pregnancy_id": "uuid",
  "estimated_due_date": "2026-12-15"
}
```

Output:

```json
[
  {
    "title": "Khám thai ban đầu",
    "week_from": 8,
    "week_to": 12,
    "scheduled_date": "2026-05-20",
    "status": "UPCOMING"
  }
]
```

### 6. Xây patient onboarding

Form gồm:

* Họ tên.
* Ngày dự sinh.
* Chấp nhận disclaimer.
* Nút tạo hồ sơ.

### 7. Xây patient dashboard

Hiển thị:

* Tuần thai.
* Tam cá nguyệt.
* Ngày dự sinh.
* Mốc tiếp theo.
* Reminder.
* Các nút điều hướng.

### 8. Xây trang timeline

Mỗi milestone hiển thị:

* Tên mốc.
* Loại.
* Khoảng tuần.
* Ngày dự kiến.
* Trạng thái.
* Mô tả.
* Nguồn hoặc nhãn mô phỏng.

### 9. Xây cập nhật ngày dự sinh

Chỉ bác sĩ được phép thực hiện.

Khi cập nhật:

* Lưu ngày cũ.
* Lưu ngày mới.
* Lưu lý do.
* Lưu người thay đổi.
* Tính lại milestone tương lai.
* Không thay đổi milestone đã hoàn thành.

---

## Kết quả cần đạt

Thai phụ có thể:

* Đăng nhập.
* Tạo hồ sơ.
* Nhập ngày dự sinh.
* Xem tuần thai.
* Xem tam cá nguyệt.
* Xem timeline.
* Xem mốc tiếp theo.

Bác sĩ có thể:

* Cập nhật ngày dự sinh.
* Hệ thống lưu history.
* Timeline được tính lại.

---

# GIAI ĐOẠN 3 — RAG VÀ AI AGENT HỎI ĐÁP

## Thời gian

Ngày 5 đến ngày 6.

## Mục tiêu

Xây chức năng hỏi đáp kiến thức thai kỳ có nguồn, đồng thời chứng minh hệ thống là Agent có khả năng gọi công cụ.

---

## Yêu cầu cần đạt

* Có knowledge base.
* Có pipeline ingest.
* Có vector search.
* Có citation.
* Có fallback khi không tìm được nguồn.
* Agent phân biệt được câu hỏi giáo dục và câu hỏi timeline.
* Agent gọi được tối thiểu ba tool.
* Agent không chẩn đoán.
* Agent không tư vấn thuốc.

---

## Những việc cần làm

### 1. Chuẩn bị tài liệu

Chọn 3–5 tài liệu đã thống nhất.

Nội dung ưu tiên:

* Kiến thức theo tuần thai.
* Dinh dưỡng.
* Vận động.
* Chuẩn bị khi khám.
* Mục đích xét nghiệm.
* Các thay đổi thông thường trong thai kỳ.

### 2. Chunk tài liệu

Mỗi chunk gồm:

```json
{
  "document_id": "DOC_001",
  "title": "Tài liệu chăm sóc thai kỳ",
  "section": "Dinh dưỡng",
  "page": 12,
  "language": "vi",
  "version": "1.0",
  "review_status": "approved",
  "content": "..."
}
```

MVP cần khoảng:

```text
50–150 chunks
```

### 3. Tạo embeddings

Quy trình:

```text
Đọc tài liệu
→ chia chunk
→ tạo embedding
→ lưu content và vector
→ lưu metadata
```

### 4. Xây retrieval service

Input:

```text
Câu hỏi người dùng
```

Output:

```text
Top 3–5 knowledge chunks liên quan
```

### 5. Xây prompt RAG

Prompt phải yêu cầu:

* Chỉ dùng context được cung cấp.
* Không tự bổ sung kiến thức ngoài tài liệu.
* Không chẩn đoán.
* Không tư vấn thuốc.
* Luôn trả citation.
* Từ chối khi context không đủ.

### 6. Xây intent router

Các intent tối thiểu:

```text
education
timeline
symptom
journal
diagnosis_request
medication_request
unsupported
```

### 7. Xây các tool

Agent cần gọi:

```text
get_pregnancy_context()
get_upcoming_milestones()
retrieve_antenatal_knowledge()
screen_danger_signs()
```

### 8. Xây LangGraph

Các node:

```text
load_context
detect_safety_intent
intent_router
retrieve_knowledge
call_timeline_tool
generate_answer
output_guardrail
save_conversation
```

### 9. Xây chat API

Request:

```json
{
  "pregnancy_id": "uuid",
  "message": "Tuần này em bé phát triển như thế nào?"
}
```

Response:

```json
{
  "answer": "...",
  "intent": "education",
  "citations": [
    {
      "document_title": "...",
      "section": "...",
      "page": 12
    }
  ],
  "safety_status": "safe"
}
```

### 10. Xây giao diện chat

Hiển thị:

* Tin nhắn người dùng.
* Câu trả lời AI.
* Citation.
* Disclaimer.
* Loading.
* Error.
* Suggested questions.

---

## Kết quả cần đạt

Agent trả lời được:

```text
Tuần thai này em bé phát triển như thế nào?
Tôi nên chuẩn bị gì cho lần khám tới?
Mốc khám tiếp theo của tôi là khi nào?
Tại sao cần thực hiện xét nghiệm này?
```

Agent phải từ chối hoặc chuyển bác sĩ khi người dùng hỏi:

```text
Tôi có bị tiền sản giật không?
Tôi nên uống thuốc gì?
Tôi có nên ngừng thuốc bác sĩ kê không?
```

---

# GIAI ĐOẠN 4 — SÀNG LỌC TRIỆU CHỨNG VÀ RED-FLAG ALERT

## Thời gian

Ngày 7 đến ngày 8.

## Mục tiêu

Xây luồng an toàn quan trọng nhất của hệ thống:

```text
Thai phụ nhập triệu chứng
→ kiểm tra rule
→ cảnh báo
→ tạo alert
→ bác sĩ xử lý
```

---

## Yêu cầu cần đạt

* Có form triệu chứng có cấu trúc.
* Có rule engine độc lập với LLM.
* Có các mức severity.
* Có template cảnh báo cố định.
* Có lưu symptom entry.
* Có tạo clinician alert.
* Doctor xem được alert.
* Có audit log.
* Red flag phải được xử lý trước RAG.

---

## Những việc cần làm

### 1. Tạo form triệu chứng

Các field mẫu:

```text
vaginal_bleeding
severe_abdominal_pain
fluid_leakage
severe_headache
vision_changes
reduced_fetal_movement
difficulty_breathing
chest_pain
fainting
severe_swelling
fever
```

### 2. Xây rule engine

Input:

```json
{
  "vaginal_bleeding": true,
  "severe_abdominal_pain": false
}
```

Output:

```json
{
  "matched": true,
  "severity": "EMERGENCY",
  "matched_rule_codes": [
    "RF_VAGINAL_BLEEDING"
  ],
  "requires_clinician_alert": true
}
```

### 3. Thống nhất mức độ

```text
NORMAL
NEEDS_REVIEW
URGENT
EMERGENCY
```

### 4. Tạo fixed alert template

Ví dụ:

```text
Đây có thể là dấu hiệu cần được đánh giá y tế ngay.

Bạn nên liên hệ cơ sở sản khoa hoặc đến cơ sở y tế gần nhất.
Không chờ phản hồi từ ứng dụng.

Ứng dụng không thể xác định chẩn đoán.
```

### 5. Kết nối với chat

Khi người dùng nhập:

```text
Tôi bị ra máu và đau bụng
```

Luồng xử lý:

```text
LLM trích xuất triệu chứng có thể có
→ yêu cầu người dùng xác nhận bằng form
→ rule engine kiểm tra
→ hiển thị fixed alert
```

LLM không trực tiếp quyết định mức độ.

### 6. Tạo symptom API

```text
POST /symptoms/extract
POST /symptoms/screen
GET  /pregnancies/{id}/symptoms
```

### 7. Tạo clinician alert

Lưu:

```text
pregnancy_id
danger_sign_event_id
severity
status
created_at
acknowledged_at
resolved_at
```

### 8. Xây doctor alert page

Hiển thị:

* Tên thai phụ.
* Thời gian.
* Mức severity.
* Triệu chứng.
* Matched rule.
* Trạng thái.
* Nút “Đã xem”.
* Nút “Đã xử lý”.

### 9. Ghi audit log

Ghi lại:

* Ai tạo alert.
* Bác sĩ nào đã xem.
* Bác sĩ nào đã xử lý.
* Thời gian xử lý.

---

## Kết quả cần đạt

Kịch bản sau phải chạy được:

```text
Patient nhập “Tôi bị ra máu”
→ hệ thống nhận dạng hoặc form xác nhận
→ rule engine match
→ cảnh báo EMERGENCY
→ tạo clinician alert
→ doctor xem alert
→ doctor acknowledge
```

---

# GIAI ĐOẠN 5 — NHẬT KÝ, DOCTOR DASHBOARD VÀ TÍCH HỢP

## Thời gian

Ngày 9 đến ngày 10.

## Mục tiêu

Hoàn thiện phần quản lý dữ liệu sức khỏe đơn giản và kết nối tất cả module thành một sản phẩm liền mạch.

---

## Yêu cầu cần đạt

* Thai phụ ghi được cân nặng.
* Thai phụ ghi được huyết áp.
* Có lịch sử dữ liệu.
* Có biểu đồ.
* Bác sĩ xem được dữ liệu.
* Có patient list.
* Có patient detail.
* Có permission check.
* Ba luồng demo chạy được từ đầu đến cuối.

---

## Những việc cần làm

### 1. Xây journal API

```text
POST /journal/weight
GET  /pregnancies/{id}/journal/weight

POST /journal/blood-pressure
GET  /pregnancies/{id}/journal/blood-pressure
```

### 2. Validation dữ liệu

Ví dụ:

* Cân nặng phải là số dương.
* Huyết áp phải gồm systolic và diastolic.
* Thời gian đo không được ở tương lai.
* Patient chỉ ghi dữ liệu cho pregnancy của chính mình.

### 3. Xây patient journal page

Có:

* Form nhập cân nặng.
* Form nhập huyết áp.
* Lịch sử.
* Biểu đồ.
* Ghi chú rằng biểu đồ không phải chẩn đoán.

### 4. Xây doctor patient list

Hiển thị:

* Tên thai phụ.
* Tuần thai.
* Ngày dự sinh.
* Mốc tiếp theo.
* Alert chưa xử lý.

### 5. Xây doctor patient detail

Hiển thị:

* Hồ sơ thai kỳ.
* Timeline.
* Reminder.
* Alert.
* Biểu đồ cân nặng.
* Biểu đồ huyết áp.
* Nút cập nhật ngày dự sinh.

### 6. Xây reminder trong ứng dụng

Reminder có:

```text
title
scheduled_date
status
pregnancy_id
milestone_id
```

Trạng thái:

```text
UPCOMING
COMPLETED
CANCELLED
```

MVP chỉ cần hiển thị trong app, không cần gửi email.

### 7. Kiểm tra phân quyền

* Patient không truy cập được doctor API.
* Patient A không xem được dữ liệu Patient B.
* Doctor chỉ xem patient được phân công.
* Chỉ doctor được cập nhật ngày dự sinh.
* Chỉ doctor được xử lý alert.

### 8. Tích hợp ba luồng demo

#### Luồng 1

```text
Login
→ onboarding
→ timeline
→ chat RAG
```

#### Luồng 2

```text
Symptom
→ red flag
→ alert
→ doctor acknowledge
```

#### Luồng 3

```text
Doctor update due date
→ timeline recalculation
→ patient sees new timeline
```

---

## Kết quả cần đạt

* Hai vai trò hoạt động.
* Patient dashboard hoạt động.
* Doctor dashboard hoạt động.
* Journal hoạt động.
* Alert hoạt động.
* Reminder hoạt động.
* Ba kịch bản demo chạy end-to-end.

---

# GIAI ĐOẠN 6 — KIỂM THỬ, DEPLOY VÀ CHUẨN BỊ DEMO

## Thời gian

Ngày 11 đến ngày 14.

## Mục tiêu

Ổn định hệ thống, phát hiện lỗi, deploy sản phẩm và chuẩn bị bản trình diễn hoàn chỉnh.

Không thêm chức năng mới trong giai đoạn này.

---

## Yêu cầu cần đạt

* Không còn lỗi blocker.
* Red-flag test đạt yêu cầu.
* RAG có citation.
* Phân quyền đúng.
* Production chạy được.
* Có dữ liệu demo.
* Có tài khoản demo.
* Có video dự phòng.
* Có slide và tài liệu.

---

## Những việc cần làm

## Ngày 11 — Kiểm thử nghiệp vụ và an toàn

### Safety test

Kiểm tra các trường hợp:

* Ra máu.
* Đau bụng dữ dội.
* Rỉ dịch.
* Đau đầu và nhìn mờ.
* Giảm cử động thai.
* Khó thở.
* Đau ngực.
* Yêu cầu chẩn đoán.
* Yêu cầu kê thuốc.
* Yêu cầu ngừng thuốc.

### Tiêu chí

* 100% red-flag cases nội bộ được phát hiện.
* Không đưa ra chẩn đoán.
* Không tư vấn thuốc.
* Không nói “không cần đi khám”.
* Cảnh báo luôn dùng template cố định.

---

## Ngày 12 — Kiểm thử RAG, API và phân quyền

### RAG test

Kiểm tra:

* Retrieval có liên quan không.
* Citation có đúng không.
* Không có nguồn thì có fallback không.
* Câu hỏi ngoài phạm vi có bị từ chối không.
* Prompt injection đơn giản có bị chặn không.

### Backend test

Kiểm tra:

* API validation.
* Permission.
* Không tạo milestone trùng.
* Cập nhật due date đúng.
* Audit log.
* Error handling.
* Không lộ secret.
* Không log PHI không cần thiết.

### Frontend test

Kiểm tra:

* Loading state.
* Error state.
* Empty state.
* Responsive cơ bản.
* Form validation.
* Route protection.

---

## Ngày 13 — Deploy

### Backend

* Deploy FastAPI.
* Deploy PostgreSQL.
* Chạy migration.
* Seed demo data.
* Cấu hình environment.
* Cấu hình CORS.
* Kiểm tra Swagger production.

### Frontend

* Deploy Next.js.
* Cấu hình backend URL.
* Kiểm tra HTTPS.
* Kiểm tra toàn bộ route.

### AI

* Cấu hình API key an toàn.
* Kiểm tra vector database production.
* Kiểm tra timeout.
* Tạo fallback khi LLM lỗi.

### Tài khoản demo

Chuẩn bị:

```text
Patient demo
Doctor demo
```

Không dùng thông tin cá nhân thật.

---

## Ngày 14 — Chuẩn bị demo và báo cáo

### Chuẩn bị video

Video 3–5 phút trình diễn:

1. Patient onboarding.
2. Timeline.
3. Chat có nguồn.
4. Khai báo red flag.
5. Doctor xem alert.
6. Doctor cập nhật ngày dự sinh.

### Chuẩn bị slide

Slide nên có:

1. Bài toán.
2. Người dùng.
3. Giải pháp.
4. Kiến trúc.
5. Agent flow.
6. RAG.
7. Red-flag safety.
8. Doctor HITL.
9. Demo.
10. Kết quả kiểm thử.
11. Giới hạn.
12. Hướng phát triển.

### Chuẩn bị tài liệu

* README.
* Architecture.
* ERD.
* API contract.
* Agent diagram.
* RAG design.
* Safety rules.
* Test report.
* Demo account.
* Deployment URL.

---

## Kết quả cần đạt

* Web app đã deploy.
* Frontend và backend kết nối được.
* Có tài khoản patient và doctor.
* Có dữ liệu mô phỏng.
* Có video demo.
* Có slide.
* Có báo cáo kiểm thử.
* Có tài liệu kiến trúc.
* Ba luồng demo chạy ổn định.

---

# 3. Phân công xuyên suốt cho bốn thành viên

## Team Leader

Phụ trách:

* Khóa phạm vi.
* Kiến trúc.
* Backlog.
* API naming.
* Review Pull Request.
* Tích hợp.
* Kiểm tra tiến độ.
* Chuẩn bị báo cáo và demo.

## Thành viên 1 — Clinical Rules và Safety

Phụ trách:

* Timeline rules.
* Red-flag rules.
* Disclaimer.
* Alert template.
* Safety test.
* Review nội dung y tế.
* Rule engine.

## Thành viên 2 — Backend, Database và Deployment

Phụ trách:

* FastAPI.
* PostgreSQL.
* Models.
* Migrations.
* API.
* Authentication.
* Permission.
* Timeline service.
* Journal.
* Alert.
* Docker.
* Deployment.

## Thành viên 3 — AI Agent, RAG và Frontend

Trong trường hợp chỉ có ba thành viên ngoài team leader, thành viên này có thể cần phối hợp chặt với leader để chia phần giao diện.

Phụ trách:

* LangGraph.
* RAG.
* Embedding.
* Retrieval.
* Prompt.
* Citation.
* Chat API integration.
* Next.js.
* Patient UI.
* Doctor UI.
* E2E test.

Nếu khối lượng frontend lớn, team leader hỗ trợ giao diện doctor dashboard và tài liệu demo.

---

# 4. Tiêu chí hoàn thành toàn bộ MVP

## Chức năng

* Có hai role.
* Có pregnancy profile.
* Có timeline.
* Có reminder.
* Có chat RAG.
* Có citation.
* Có red-flag screening.
* Có doctor alert.
* Có weight journal.
* Có blood pressure journal.
* Có doctor dashboard.
* Có due-date update.

## An toàn

* Không chẩn đoán.
* Không kê thuốc.
* Không tư vấn ngừng thuốc.
* Red flag do rule engine quyết định.
* Fixed emergency template.
* Disclaimer hiển thị rõ.
* Có doctor HITL.

## Kỹ thuật

* FastAPI.
* Next.js.
* PostgreSQL.
* pgvector.
* LangGraph.
* Docker.
* API documentation.
* Migration.
* Permission.
* Audit log.

## Kiểm thử

* Red-flag tests đạt 100% trên bộ test nội bộ.
* RAG trả lời có citation.
* Ba luồng E2E chạy được.
* Không có lỗi blocker.
* Main branch deploy được.

---

# 5. Nguyên tắc cắt giảm khi chậm tiến độ

Cắt theo thứ tự:

1. Đa ngôn ngữ.
2. Email reminder.
3. Tạo danh sách câu hỏi đi khám.
4. Tóm tắt nhật ký bằng AI.
5. Conversation memory nâng cao.
6. Biểu đồ nâng cao.
7. Cử động thai.
8. Bác sĩ duyệt từng reminder.

Không được cắt:

* Hai role.
* Pregnancy profile.
* Timeline.
* RAG có nguồn.
* Red-flag rule engine.
* Fixed alert.
* Doctor alert.
* Disclaimer.
* Phân quyền.
* Ba luồng demo chính.
