

Bài thực hành này triển khai đầy đủ quy trình phân tích cú pháp phụ thuộc (dependency parsing) bằng thư viện spaCy. Mình đã thực hiện các bước chính như sau:

### 1. Các bước triển khai
- Cài đặt spaCy và tải mô hình `en_core_web_md`.
- Viết hàm hiển thị cấu trúc dependency bằng `displacy`, chỉnh lại để chạy ổn định trên Colab.
- Xây dựng các hàm cần thiết: in bảng token, tìm SVO, tìm tính từ bổ nghĩa, xác định động từ chính (ROOT), tự viết noun chunk, và tìm đường đi từ token đến ROOT.
- Chạy thử trên nhiều câu ví dụ để kiểm tra tính chính xác.

### 2. Cách chạy và log kết quả
- Chạy lần lượt các cell: cài đặt → import → định nghĩa hàm → phần demo.
- Colab sẽ hiển thị biểu đồ dependency, bảng token, SVO, noun-chunk và path đến ROOT.
- Kết quả cũng được lưu vào file `/content/dependency_parse_example.txt`.

### 3. Nhận xét kết quả
- displaCy hiển thị rõ cấu trúc câu, dễ thấy quan hệ nsubj, dobj, amod,...
- Hàm SVO hoạt động đúng với cả câu đơn lẫn câu ghép.
- Noun-chunk tự viết cho kết quả khá gần với spaCy bản chuẩn.
- Path-to-root cho thấy mối quan hệ điều khiển giữa các từ trong câu.

### 4. Khó khăn & cách xử lý
- displaCy lỗi khi `options=None` → khắc phục bằng cách ép `options={}`.
- Các câu phức tạp dễ làm SVO bị lệch → xử lý bằng duyệt từng child của từng động từ.
- Noun-chunk đơn giản nên chưa bao quát hết các cấu trúc hiếm.

