# Test Cases — Bảng trường hợp kiểm thử

> **Hướng dẫn**: Viết tối thiểu **20 TC** phủ đủ các chức năng chính (REQ-01 → REQ-08).
> Xem [examples/sample-test-case.md](../examples/sample-test-case.md) để hiểu cách viết TC tốt.
> Tự tổ chức và phân nhóm test case theo cách hợp lý nhất.

| Thông tin | |
|---|---|
| **Nhóm** | `Group 25` |
| **Ngày tạo** | `<!-- DD/MM/YYYY -->` |
| **Hệ thống** | https://stqa.rbc.vn |
| **Tham chiếu** | SRS v1.0 |

---

## Bước 1: Mô hình hóa miền đầu vào — Input Domain Modeling (IDM)

> 📖 **Textbook:** Chương 6 — *Input Domain Modeling*, Paul Ammann & Jeff Offutt.
>
> **Trước khi viết Test Case**, nhóm **phải** phân tích miền đầu vào bằng bảng IDM bên dưới.
> Mỗi chức năng cần xác định: **Đặc tính (Characteristic)**, **Phân vùng (Block/Partition)**, và **Giá trị đại diện (Value)**.

### IDM — Đăng nhập (REQ-01)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Email có tồn tại trong DB? | Có | `librarian@library.com` | Đăng nhập thành công |
| | Không | `noone@email.com` | Thông báo lỗi |
| Mật khẩu có đúng? | Đúng | `admin123` | Đăng nhập thành công |
| | Sai | `wrongpass` | Thông báo lỗi |
| Ô nhập có rỗng? | Không rỗng | (giá trị bất kỳ) | Xử lý bình thường |
| | Rỗng | `""` | Thông báo "Vui lòng nhập..." |

### IDM — View book list (REQ-02)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Role of the logged-in user? | Librarian | `librarian@library.com` | Views all 20 books with complete details |
| | Member | `ba.nguyen@email.com` | Views all 20 books with complete details |
| Display status of the book? | Available | BOOK001, BOOK002 | Displays status as "Available" |
| | Borrowed | BOOK003 (currently borrowed by MEM002) | Displays status as "Borrowed" |
| | Lost | BOOK007, BOOK020 | Displays status as "Lost" |
| Is the displayed information complete? | Complete with 5 fields: title, author, genre, year, status | BOOK001 | Displays: "Lập trình Flutter cơ bản", "Nguyễn Minh Đức", "Công nghệ", "2023", "Available" |
| Real-time update after an action? | After borrowing a book | Borrow BOOK001 | Status of BOOK001 immediately changes to "Borrowed" without needing a refresh |
| | After returning a book | Return BOOK003 | Status of BOOK003 immediately changes to "Available" |

---

### IDM — Tìm kiếm sách (REQ-03)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Từ khóa có tồn tại trong DB? | Có (tên sách) | `"Flutter"` | Hiển thị sách chứa "Flutter" |
| | Có (tên tác giả) | `"Nguyễn"` | Hiển thị sách của tác giả Nguyễn |
| | Không | `"XYZ123"` | Danh sách rỗng |
| Phân biệt HOA/thường? | Chữ thường | `"flutter"` | Kết quả giống "Flutter" |
| | Chữ HOA | `"FLUTTER"` | Kết quả giống "Flutter" |

### IDM — Mượn sách (REQ-04, REQ-05)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Trạng thái sách? | Có sẵn | BOOK001 | Cho phép mượn |
| | Đang mượn | BOOK003 | Không cho phép |
| | Thất lạc | BOOK007 | Không cho phép |
| Trạng thái thành viên? | Hoạt động | MEM002 | Cho phép mượn |
| | Tạm ngưng | MEM004 | Từ chối, thông báo lỗi |
| | Hết hạn | MEM005 | Từ chối, thông báo lỗi |
| Số sách đang mượn? | < 3 (BVA: 0, 1, 2) | MEM006 (0 sách) | Cho phép mượn |
| | = 3 (BVA: giới hạn) | MEM đã mượn 3 sách | Từ chối, thông báo vượt giới hạn |

### IDM — Trả sách & Xử lý quá hạn (REQ-05, REQ-06)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Trạng thái phiếu mượn? | Đang mượn | BR003 | Cho phép trả sách |
| | Đã trả | BR002 | Không hiển thị thao tác trả |
| Thời điểm trả sách? | Trước / Đúng hạn | Ngày trả <= `dueDate` | Trả thành công, trạng thái "Có sẵn" |
| | Quá hạn | Ngày trả > `dueDate` | Trả thành công, hiển thị cảnh báo quá hạn |

### IDM — Quản lý thành viên (REQ-07)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Quyền thực hiện? | Thủ thư | `librarian@library.com` | Có quyền thêm thành viên |
| | Thành viên | `ba.nguyen@email.com` | Không có quyền truy cập |
| Định dạng Email? | Hợp lệ (có `@` và `.`) | `luc1f3r@library.com` | Xử lý bình thường |
| | Không hợp lệ | `user@domain` | Báo lỗi định dạng email |
| Email đã tồn tại trong DB?| Chưa tồn tại | `luc1f3r@library.com` | Tạo thành viên thành công |
| | Đã tồn tại | `ba.nguyen@email.com` | Thông báo lỗi email đã tồn tại |

### IDM — Tra cứu phiếu mượn (REQ-08)

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
|---|---|---|---|
| Vai trò người tra cứu? | Thủ thư | `librarian@library.com` | Xem được tất cả phiếu mượn của hệ thống |
| | Thành viên | `ba.nguyen@email.com` | Chỉ xem được phiếu của chính mình |
| Tính riêng tư của thành viên? | Xem phiếu của mình | MEM002 xem BR001 | Hiển thị chi tiết phiếu mượn |
| | Xem phiếu người khác | MEM002 xem BR002 | Không hiển thị / Không cho phép truy cập |

---

## Bước 2: Test Cases

| Mã TC | Mục tiêu kiểm thử | Tiền điều kiện | Bước thực hiện | Dữ liệu đầu vào | Kết quả mong đợi | REQ | Kỹ thuật |
|-------|-------------------|---------------|---------------|-----------------|------------------|-----|---------|
| **TC-01** | Đăng nhập thành công với tài khoản Thành viên | Ở trang Đăng nhập | 1. Nhập email.<br>2. Nhập mật khẩu.<br>3. Nhấn "Đăng nhập". | Email: `ba.nguyen@email.com`<br>Pass: `password123` | Chuyển sang trang chủ. Tên và vai trò hiển thị trên AppBar. | REQ-01 | EP |
| **TC-02** | Đăng nhập thành công với tài khoản Thủ thư | Ở trang Đăng nhập | 1. Nhập email.<br>2. Nhập mật khẩu.<br>3. Nhấn "Đăng nhập". | Email: `librarian@library.com`<br>Pass: `admin123` | Chuyển sang trang chủ. Có thêm các menu dành riêng cho Thủ thư. | REQ-01 | EP |
| **TC-03** | Đăng nhập thất bại do sai mật khẩu | Ở trang Đăng nhập | 1. Nhập email đúng.<br>2. Nhập mật khẩu sai.<br>3. Nhấn "Đăng nhập". | Email: `ba.nguyen@email.com`<br>Pass: `wrongpass` | Hiển thị thông báo lỗi "Mật khẩu không đúng". | REQ-01 | EP |
| **TC-04** | Đăng nhập thất bại do tài khoản không tồn tại | Ở trang Đăng nhập | 1. Nhập email không có trong danh sách.<br>2. Nhập mật khẩu.<br>3. Nhấn "Đăng nhập". | Email: `noone@email.com`<br>Pass: `123456` | Hiển thị thông báo lỗi "Không tìm thấy thành viên". | REQ-01 | EP |
| **TC-05** | Đăng nhập thất bại do bỏ trống trường dữ liệu | Ở trang Đăng nhập | 1. Bỏ trống email hoặc mật khẩu.<br>2. Nhấn "Đăng nhập". | Email: `""`<br>Pass: `""` | Hiển thị thông báo lỗi "Vui lòng nhập email và mật khẩu". | REQ-01 | BVA |
| **TC-06** | Hiển thị danh sách sách và trạng thái mặc định | Đã đăng nhập bằng `biet.hoang@email.com` | 1. Chuyển sang tab "Sách".<br>2. Quan sát danh sách sách. | (Không có) | Hiển thị đủ 20 đầu sách. BOOK003 hiển thị trạng thái "Đang mượn", BOOK001 hiển thị "Có sẵn". | REQ-02 | EP |
| **TC-07** | Tìm kiếm sách theo tên (không phân biệt hoa/thường) | Đang ở tab "Sách" | 1. Nhập từ khóa vào ô tìm kiếm.<br>2. Nhấn "Tìm kiếm". | Từ khóa: `"FLUTTER"` | Hiển thị sách BOOK001 (Lập trình Flutter cơ bản). | REQ-03 | EP |
| **TC-08** | Tìm kiếm sách theo tác giả | Đang ở tab "Sách" | 1. Nhập tên tác giả vào ô tìm kiếm.<br>2. Nhấn "Tìm kiếm". | Từ khóa: `"Nguyễn Minh Đức"` | Hiển thị BOOK001 và BOOK009. | REQ-03 | EP |
| **TC-09** | Tìm kiếm sách không có kết quả | Đang ở tab "Sách" | 1. Nhập từ khóa không tồn tại.<br>2. Nhấn "Tìm kiếm". | Từ khóa: `"Sách Nấu Ăn"` | Hiển thị thông báo "Không tìm thấy sách". | REQ-03 | EP |
| **TC-10** | Mượn sách thành công | Đăng nhập bằng `biet.hoang@email.com` (Đang HĐ) | 1. Chọn BOOK001 đang "Có sẵn".<br>2. Nhấn "Mượn sách". | Sách: `BOOK001` | Trạng thái sách chuyển thành "Đang mượn". Hệ thống sinh phiếu mượn mới. | REQ-04 | EP |
| **TC-11** | Mượn sách thất bại do sách đã có người mượn | Đăng nhập bằng `biet.hoang@email.com` | 1. Tìm BOOK003 (Đang mượn).<br>2. Kiểm tra thao tác mượn. | Sách: `BOOK003` | Nút "Mượn sách" bị vô hiệu hóa hoặc ẩn đi. | REQ-04 | EP |
| **TC-12** | Mượn sách thất bại do tài khoản bị tạm ngưng | Đăng nhập bằng `cu.le@email.com` (Tạm ngưng) | 1. Chọn BOOK001 đang "Có sẵn".<br>2. Nhấn "Mượn sách". | Sách: `BOOK001` | Từ chối mượn, thông báo tài khoản bị tạm ngưng. | REQ-04 | EP |
| **TC-13** | Mượn sách thất bại do tài khoản hết hạn | Đăng nhập bằng `binh.pham@email.com` (Hết hạn) | 1. Chọn BOOK001 đang "Có sẵn".<br>2. Nhấn "Mượn sách". | Sách: `BOOK001` | Từ chối mượn, thông báo tài khoản đã hết hạn. | REQ-04 | EP |
| **TC-14** | Mượn sách thất bại do vượt quá giới hạn 3 cuốn | Đăng nhập `biet.hoang@email.com`, mượn liên tiếp 3 sách thành công | 1. Chọn sách "Có sẵn" thứ 4.<br>2. Nhấn "Mượn sách". | Sách thứ 4 bất kỳ | Từ chối mượn, thông báo "Thành viên đã đạt giới hạn 3 sách". | REQ-04 | BVA |
| **TC-15** | Trả sách thành công (đúng hạn) | Đăng nhập bằng `biet.hoang@email.com` | 1. Vào tab Mượn/Trả.<br>2. Chọn phiếu BR003.<br>3. Nhấn "Trả sách". | Phiếu: `BR003` | Sách BOOK013 chuyển về trạng thái "Có sẵn". Không có cảnh báo lỗi. | REQ-05 | EP |
| **TC-16** | Trả sách có cảnh báo quá hạn | Đăng nhập bằng `ba.nguyen@email.com` | 1. Vào tab Mượn/Trả.<br>2. Chọn phiếu BR001 (Quá hạn).<br>3. Nhấn "Trả sách". | Phiếu: `BR001` | Sách BOOK003 chuyển về "Có sẵn". Hiển thị cảnh báo trả sách quá hạn. | REQ-05 | BVA |
| **TC-17** | Thủ thư kiểm tra quá hạn hệ thống | Đăng nhập bằng `librarian@library.com` | 1. Vào chức năng Thủ thư.<br>2. Nhấn "Kiểm tra quá hạn". | (Không có) | Phiếu BR001 tự động cập nhật trạng thái thành "Quá hạn". | REQ-06 | EP |
| **TC-18** | Thêm thành viên mới thành công | Đăng nhập bằng `librarian@library.com`, tab Thành viên | 1. Nhấn "Thêm thành viên".<br>2. Nhập thông tin hợp lệ.<br>3. Nhấn "Lưu". | Tên: `Long`, Email: `luc1f3r@library.com`, SĐT: `0987654321` | Lưu thành viên mới thành công, tài khoản mới được ghi nhận. | REQ-07 | EP |
| **TC-19** | Thêm thành viên thất bại do email không hợp lệ | Đăng nhập bằng `librarian@library.com`, tab Thành viên | 1. Nhấn "Thêm thành viên".<br>2. Nhập email sai định dạng.<br>3. Nhấn "Lưu". | Email: `luc1f3r@domain` (Thiếu dấu chấm) | Từ chối lưu, hệ thống báo lỗi định dạng email. | REQ-07 | EP |
| **TC-20** | Thêm thành viên thất bại do trùng email | Đăng nhập bằng `librarian@library.com`, tab Thành viên | 1. Nhấn "Thêm".<br>2. Nhập email đã tồn tại ở list.<br>3. Nhấn "Lưu". | Email: `ba.nguyen@email.com` | Từ chối lưu, thông báo lỗi email đã tồn tại. | REQ-07 | EP |
| **TC-21** | Kiểm tra quyền tra cứu phiếu mượn | Đăng nhập lần lượt `librarian@library.com` và `dam.tran@email.com` | 1. Vào tab Mượn/Trả.<br>2. Kiểm tra danh sách phiếu. | 2 tài khoản trên | Thủ thư thấy toàn bộ phiếu. `dam.tran@email.com` chỉ thấy phiếu của chính mình. | REQ-08 | EP |
---

## Tổng hợp

| Nhóm chức năng | Số TC | REQ phủ | Kỹ thuật IDM áp dụng |
|----------------|-------|---------|----------------------|
| Đăng nhập tài khoản | 5 | REQ-01 | Phân lớp tương đương (EP), Phân tích giá trị biên (BVA) |
| Xem và Tìm kiếm sách | 4 | REQ-02, REQ-03 | Phân lớp tương đương (EP) |
| Giao dịch Mượn & Trả sách | 7 | REQ-04, REQ-05 | Phân lớp tương đương (EP), Phân tích giá trị biên (BVA) |
| Quản lý của Thủ thư & Tra cứu | 5 | REQ-06, REQ-07, REQ-08 | Phân lớp tương đương (EP) |
| **Tổng số lượng TC** | **21** | **REQ-01 → REQ-08** | **EP, BVA** |

---
