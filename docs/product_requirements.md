# Product Requirements — Prenatal Care Agent MVP

## Mục tiêu

Xây dựng ứng dụng web hỗ trợ thai phụ theo dõi thai kỳ, xem timeline,
hỏi đáp kiến thức có nguồn, khai báo triệu chứng và gửi cảnh báo cho bác sĩ.

## Vai trò

- PATIENT
- DOCTOR

## Chức năng bắt buộc

### Patient

- Đăng nhập
- Tạo hồ sơ thai kỳ
- Nhập ngày dự sinh
- Xem tuần thai và tam cá nguyệt
- Xem timeline
- Xem mốc tiếp theo
- Hỏi AI có trích nguồn
- Khai báo triệu chứng
- Nhận cảnh báo red flag
- Ghi cân nặng
- Ghi huyết áp

### Doctor

- Đăng nhập
- Xem danh sách thai phụ
- Xem chi tiết thai kỳ
- Xem timeline
- Xem nhật ký sức khỏe
- Xem cảnh báo
- Đánh dấu cảnh báo đã xem hoặc đã xử lý
- Cập nhật ngày dự sinh

## Không triển khai trong MVP

- Chẩn đoán
- Kê thuốc
- Đọc xét nghiệm
- Đọc ảnh siêu âm
- Mobile app
- Push notification
- Multi-agent
- Fine-tuning
- Dữ liệu bệnh nhân thật

## Nguyên tắc an toàn

Rule-first, LLM-second, Doctor-overrides-all.

## Trạng thái phạm vi

MVP scope locked: 01/08/2026