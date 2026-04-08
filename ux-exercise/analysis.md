# UX Exercise — Vietnam Airlines · Chatbot NEO

## Sản phẩm: Vietnam Airlines — Chatbot NEO (hỗ trợ khách hàng, tra cứu chuyến bay)

---

## Marketing hứa gì?

- Chatbot hỗ trợ khách hàng 24/7, giải đáp thông tin chuyến bay, đặt vé, đổi vé, hành lý, check-in, Lotusmiles
- Trả lời nhanh, tự động, không cần chờ tổng đài
- Chuyên môn: "giải đáp các thông tin đến khách hàng"

---

## 4 Paths

### Path 1 — Khi AI đúng
- **Tình huống:** Hỏi các intent phổ biến: đặt vé, đổi vé, hành lý, check-in, Lotusmiles
- **UI phản hồi:** Trả lời dạng FAQ chuẩn (template-based), có thể kèm source/document. Nhập được cả text lẫn voice.
- **User có biết AI đang đúng không?** Không có explicit confidence score — confirmation hoàn toàn implicit, user tự đánh giá câu trả lời có đúng không
- **Vấn đề:** Không có confirm loop ("Bạn có muốn tiếp tục?") → user không biết có nên tin kết quả không. Phản hồi **chậm** dù availability 24/7.

### Path 2 — Khi AI không chắc
- **Tình huống:** Hỏi chủ đề ngoài scope hoặc câu hỏi mơ hồ
- **Chatbot làm:** Gửi tin nhắn "không hỗ trợ chủ đề này" → forward sang số điện thoại và email CSKH
- **Không có:** Hỏi lại để clarify intent (multi-turn reasoning yếu), "Did you mean...?", đưa ra giải pháp thay thế
- **Nhận xét:** Nhiều trường hợp **nằm trong khả năng xử lý nhưng NEO vẫn từ chối** → escalate thẳng sang CSKH

### Path 3 — Khi AI sai
- **User biết bằng cách nào?** Phải tự nhận ra — hệ thống không có flag lỗi, không disclaimer độ chính xác tự động
- **Sửa bằng cách nào?** Không có flow sửa trực tiếp trong conversation. User buộc phải: hỏi lại (rephrase) → hoặc rời chatbot tìm thông tin thủ công → hoặc liên hệ support
- **Path này gần như không tồn tại:** Khi AI sai, hệ thống chỉ phản hồi "nằm ngoài phạm vi tác vụ", không hỏi lại để làm rõ ngữ cảnh, không đưa câu trả lời thay thế

### Path 4 — Khi user mất niềm tin
- **Có exit không?** Có — forward sang hotline, email, helpdesk page
- **Vấn đề:** Fallback nằm **ngoài chatbot**, không embedded trong flow hội thoại. Không có nút "Talk to human" ngay trong chat.
- **Dễ tìm không?** Trung bình — phải scroll hoặc chuyển trang mới thấy

---

## Path mạnh nhất

**Path 1 — Khi AI đúng:** Với các intent phổ biến (đặt vé, hành lý, check-in) chatbot trả lời đủ thông tin, template chuẩn, có source kèm theo.

---

## Path yếu nhất

**Path 2 + 3 — Không chắc & Sai:** Multi-turn reasoning gần như không có. Gặp câu hỏi mơ hồ hoặc hơi ngoài scope → từ chối ngay thay vì hỏi lại. Khi sai không có cơ chế recovery trong conversation. **Đây là path được chọn để sketch to-be.**

---

## Gap marketing vs thực tế

| | Nội dung |
|--|---------|
| **Marketing hứa** | Chatbot chuyên môn giải đáp thông tin khách hàng 24/7, tự động, nhanh |
| **Thực tế** | Chỉ đáp ứng ~40% những gì được hứa. Thực chất là bot chuyển tiếp công việc sang nhân viên CSKH. Phản hồi chậm. Sẵn sàng trả lời món ăn trên máy bay nhưng từ chối liệt kê danh sách chuyến bay. |
| **Gap lớn nhất** | Marketing nói "giải đáp thông tin" nhưng thực tế NEO không có khả năng clarify intent → mọi câu hỏi hơi phức tạp đều bị đẩy sang CSKH. Bot chỉ hoạt động tốt với FAQ cứng, không xử lý được ngữ cảnh động. |
