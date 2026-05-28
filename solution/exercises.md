# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature = 0.0, câu trả lời mang tính logic, khuôn mẫu và lặp lại nếu hỏi nhiều lần. Khi tăng dần lên 0.5 và 1.0, văn phong trở nên tự nhiên, đa dạng và sinh động hơn. Tại mức 1.5, mô hình có xu hướng "ảo giác", dùng từ ngữ kỳ quặc hoặc ngữ pháp lộn xộn, thiếu tính gắn kết.
**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Đối với chatbot hỗ trợ khách hàng, em sẽ đặt temperature ở mức thấp, khoảng 0.1 đến 0.3. Mục đích là để đảm bảo câu trả lời luôn ổn định, chính xác, bám sát tài liệu hướng dẫn (FAQ) của công ty và tránh rủi ro chatbot bịaa thông tin sai lệch gây nhầm lẫn cho khách hàng.
---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Khoảng 16-17 lần
**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi: Thực hiện các tác vụ phức tạp đòi hỏi khả năng tư duy logic sâu, lập luận đa bước, viết mã nguồn (coding) hoặc phân tích ngữ nghĩa khó. Việc sai lệch gây hậu quả nghiêm trọng. Ví dụ như xác định lời khuyên cho bệnh nhân.

GPT-4o-mini tốt hơn khi: Xử lý các tác vụ số lượng lớn, lặp đi lặp lại và đơn giản như: phân loại cảm xúc văn bản (sentiment analysis), tóm tắt tin tức, trích xuất thực thể (data extraction) hoặc chatbot giao tiếp thông thường.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng giao tiếp trực tiếp với người dùng cuối (như chatbot, trợ lý ảo) vì nó làm giảm đáng kể Time-To-First-Byte (thời gian phản hồi ký tự đầu tiên). Việc nhìn thấy chữ hiện ra liên tục giúp người dùng cảm thấy hệ thống phản hồi nhanh và giữ chân họ không rời đi. Ngược lại, non-streaming lại phù hợp hơn đối với các tác vụ xử lý tự động chạy ngầm (background jobs) như: phân tích hàng loạt tài liệu, xử lý dữ liệu API giữa hệ thống với hệ thống, hoặc khi cần nhận toàn bộ cấu trúc JSON chuẩn xác để lưu vào cơ sở dữ liệu trước khi chuyển sang bước tiếp theo.

## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
