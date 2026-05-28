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
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít thay đổi giữa các lần gọi. Khi tăng lên 0.5 và 1.0, câu trả lời bắt đầu đa dạng, tự nhiên và có nhiều cách diễn đạt hơn. Ở mức 1.5, phản hồi sáng tạo hơn nhưng cũng dễ lan man hoặc kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2 đến 0.3 cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời nhất quán, an toàn và bám sát chính sách hỗ trợ, nhưng vẫn đủ tự nhiên để người dùng không cảm thấy quá máy móc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload này có khoảng 10.000 x 3 x 350 = 10.500.000 token mỗi ngày. Theo bảng giá trong `template.py`, GPT-4o có giá input/output lần lượt là 5.00/20.00 USD trên 1M token, còn GPT-4o-mini là 0.150/0.600 USD trên 1M token. Vì cả giá input và output của GPT-4o đều cao hơn GPT-4o-mini khoảng 33,3 lần, nên GPT-4o cũng đắt hơn GPT-4o-mini khoảng 33,3 lần cho workload này.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng dùng khi tác vụ cần chất lượng suy luận cao, ví dụ phân tích tài liệu phức tạp, tư vấn chuyên sâu, hoặc xử lý yêu cầu quan trọng có ảnh hưởng trực tiếp đến người dùng. GPT-4o-mini phù hợp hơn cho các tác vụ số lượng lớn, rủi ro thấp như chatbot FAQ, phân loại nội dung đơn giản, tóm tắt ngắn hoặc gợi ý câu trả lời ban đầu.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi có thể dài hoặc người dùng cần cảm giác hệ thống đang xử lý ngay lập tức, ví dụ chatbot, trợ lý viết nội dung, giải thích bài học hoặc phân tích tài liệu dài. Việc hiển thị từng phần giúp giảm cảm giác chờ đợi và làm trải nghiệm giống hội thoại thật hơn. Non-streaming phù hợp hơn khi cần nhận toàn bộ kết quả trước khi hiển thị, ví dụ trả về JSON, gọi API nội bộ, chấm điểm tự động, hoặc các tác vụ mà kết quả chỉ hữu ích khi đã hoàn chỉnh.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
