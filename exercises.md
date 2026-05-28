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
> *Khi temperature tăng dần, nội dung câu trả lời dịch chuyển tu chính xác cao sang sự đa dạng và ngẫu nhiên. Ở mức thấp (0.0 và 0.5), chatbot giữ nguyên thông tin cốt lõi về kích thước Hang Sơn Đoòng là 5 km, nhưng khi đạt mức cao (1.5), mô hình bắt đầu "sáng tạo" và đưa ra con số 9 km*

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *0.0 vì mô hình sẽ luôn chọn từ có xác suất cao nhất*

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> *16.7 lần*

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> *Các hệ thống đòi hỏi khả năng suy luận logic chuyên sâu, đọc hiểu các tài liệu ngữ cảnh dài, xử lý cấu trúc dữ liệu ngặt nghèo và yêu cầu độ chính xác tuyệt đối thì GPT-4o là xứng đáng. Còn các tác vụ như: Tóm tắt bài báo, phân loại cảm xúc bình luận (Sentiment Analysis) của hàng triệu khách hàng, hoặc chatbot phản hồi nhanh các câu hỏi thường gặp thì GPT-4o-mini*

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> *Streaming là yếu tố sống còn trong các ứng dụng Chatbot tương tác trực tiếp hoặc trợ lý ảo (như ChatGPT), nơi người dùng cần phản hồi tức thì để duy trì mạch hội thoại và giảm "thời gian chờ đợi cảm nhận" (perceived latency) khi AI phải sinh một đoạn văn dài. Ngược lại, non-streaming lại phù hợp hơn đối với các tác vụ xử lý ngầm (background jobs) hoặc tích hợp hệ thống (API-to-API) không có sự hiện diện trực tiếp của con người, chẳng hạn như trích xuất dữ liệu hàng loạt (Batch Parsing), phân tích cảm xúc văn bản, dịch thuật tự động cả tài liệu, hoặc khi hệ thống cần kiểm tra, định dạng lại toàn bộ dữ liệu đầu ra (JSON/XML) một cách trọn vẹn trước khi chuyển tiếp sang bước xử lý tiếp theo.*


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
