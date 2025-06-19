# RSA
# Nguyễn Đình Tài
# Giới thiệu
ThuatToanRSA là một ứng dụng web đơn giản giúp người dùng mã hóa và giải mã dữ liệu, hoặc tạo và xác thực chữ ký số bằng thuật toán RSA (Rivest–Shamir–Adleman) – một trong những thuật toán mã hóa công khai phổ biến và an toàn nhất hiện nay. RSA cho phép bảo vệ tính bí mật, toàn vẹn và xác thực của dữ liệu thông qua cơ chế khóa công khai và khóa riêng biệt, rất thích hợp cho các ứng dụng bảo mật như chữ ký số, xác thực tài liệu và truyền thông an toàn trên Internet.
# Chức năng cơ bản 
📌 1. Giao diện: Ký Số Tài Liệu An Toàn (Hình thứ hai)
👉 Đây là giao diện dành cho người gửi, với chức năng chính là tạo chữ ký số cho tài liệu.

🔧 Chức năng chính:
Tải lên file tài liệu (Choose File)
Người dùng chọn một tập tin cần ký (PDF, DOCX, TXT…).
Tạo chữ ký số cho tài liệu
Khi nhấn nút "Tải lên & Ký số":
Ứng dụng tính hash của nội dung file.
Sử dụng khóa riêng RSA để tạo chữ ký số (dạng hex).
Trả về kết quả gồm:
Tệp gốc
Chữ ký số (hex)
Khóa công khai (PEM)
🎯 Mục tiêu:
Đảm bảo rằng nội dung tài liệu được ký bởi đúng người gửi và không bị thay đổi trong quá trình truyền đi.
📌 2. Giao diện: Trình Xác Thực Chữ Ký Số (Hình thứ nhất)
👉 Đây là giao diện dành cho người nhận, giúp kiểm tra tính hợp lệ của chữ ký số.
🔧 Chức năng chính:
Tải lên file gốc (Choose File)
Người nhận tải lên file tài liệu gốc đã được ký.
Nhập chữ ký số (dạng Hex)
Dán chữ ký số (mã hex) được người gửi cung cấp.
Nhập khóa công khai (PEM)
Dán khóa công khai của người gửi (được gửi kèm theo hoặc công khai).
Xác thực chữ ký số
Nhấn nút "Xác thực" để kiểm tra:
Hash của file gốc có khớp với kết quả giải mã chữ ký không.
Thông báo “Xác thực thành công” hoặc “Không hợp lệ” tùy kết quả.
🎯 Mục tiêu:
Kiểm tra xem:
File có bị chỉnh sửa không?
Chữ ký số có đúng là do người gửi tạo ra không?
# Kỹ thuật và công nghệ sử dụng Ngôn ngữ lập trình
Các Kỹ Thuật Sử Dụng
🔐 1. Mật mã học bất đối xứng – RSA
Vai trò: Là thuật toán lõi của hệ thống.
Dùng để:
Ký số tài liệu bằng khóa riêng.
Xác thực chữ ký số bằng khóa công khai.
Lý do chọn RSA: Rất phổ biến, dễ triển khai, phù hợp với chữ ký số.
![image](https://github.com/user-attachments/assets/e04c6731-3040-4167-9102-4f1012edb5cb)
🔎 2. Hàm băm – SHA-256 (hoặc tương đương)
Vai trò: Tính toán giá trị băm (hash) của tài liệu.
Dùng để:
Tạo "dấu vân tay" cho file.
So sánh với chữ ký số sau khi giải mã để kiểm tra toàn vẹn.
Tính chất: Không thể đảo ngược, nhạy cảm với thay đổi nhỏ.
🧾 3. Chữ ký số (Digital Signature)
![image](https://github.com/user-attachments/assets/322b41c1-6941-4437-af2b-f88fa6fc209f)

Định dạng: Dạng hex sau khi ký.
Quy trình:
Băm nội dung file → mã hóa hash bằng RSA Private Key → tạo chữ ký.
Người nhận: Giải mã chữ ký bằng Public Key, so sánh với hash tự tính từ file.
Mục đích: Xác thực người gửi + bảo đảm dữ liệu không bị chỉnh sửa.
