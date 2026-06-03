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
| **TC-06** | Hiển thị danh sách sách và trạng thái mặc định | Đã đăng nhập bằng `biet.hoang@email.com` | 1. Chuyển sang tab "Sách".<br>2. Quan sát danh sách sách. | (Không có) | Hiển thị đủ 20 đầu sách. BOOK003 hiển thị "Đang mượn", BOOK001 hiển thị "Có sẵn". | REQ-02 | EP |
| **TC-07** | Tìm kiếm sách bằng chữ thường/bình thường | Đang ở tab "Sách" | 1. Nhập từ khóa chữ thường vào ô tìm kiếm.<br>2. Nhấn "Tìm kiếm". | Từ khóa: `"lập trình"` | Hiển thị sách BOOK001 (Lập trình Flutter cơ bản). Không phân biệt chữ hoa/thường. | REQ-03 | EP |
| **TC-08** | Tìm kiếm sách bằng chữ toàn bộ IN HOA | Đang ở tab "Sách" | 1. Nhập từ khóa IN HOA vào ô tìm kiếm.<br>2. Nhấn "Tìm kiếm". | Từ khóa: `"FLUTTER"` | Hiển thị sách BOOK001 (Lập trình Flutter cơ bản). Không phân biệt chữ hoa/thường. | REQ-03 | EP |
| **TC-09** | Tìm kiếm sách không có kết quả | Đang ở tab "Sách" | 1. Nhập từ khóa không tồn tại.<br>2. Nhấn "Tìm kiếm". | Từ khóa: `"Sách Nấu Ăn"` | Hiển thị thông báo "Không tìm thấy sách". | REQ-03 | EP |
| **TC-10** | Lọc sách theo thể loại đúng định dạng (Có viết hoa) | Đang ở tab "Sách" | 1. Nhập thể loại vào ô Lọc.<br>2. Quan sát kết quả. | Lọc: `"Công nghệ"` | Hiển thị danh sách các sách thuộc nhóm Công nghệ. | REQ-03 | EP |
| **TC-11** | Lọc sách theo thể loại không phân biệt hoa thường | Đang ở tab "Sách" | 1. Nhập thể loại chữ thường vào ô Lọc.<br>2. Quan sát kết quả. | Lọc: `"công nghệ"` | Hiển thị danh sách các sách thuộc nhóm Công nghệ. | REQ-03 | EP |
| **TC-12** | Lọc kết hợp Tìm kiếm không ra kết quả | Đang ở tab "Sách" | 1. Nhập tìm "Flutter".<br>2. Nhập lọc "Kinh tế". | Tìm: `"Flutter"`<br>Lọc: `"Kinh tế"` | Hiển thị "Không tìm thấy sách" do xung đột điều kiện. | REQ-03 | EP |
| **TC-13** | Mượn sách thành công | Đăng nhập bằng `biet.hoang@email.com` | 1. Chọn BOOK001 đang "Có sẵn".<br>2. Nhấn "Mượn sách" (Nút +). | Sách: `BOOK001` | Trạng thái sách chuyển thành "Đang mượn". Hệ thống sinh phiếu mượn mới. | REQ-04 | EP |
| **TC-14** | Mượn sách thất bại do sách đã có người mượn | Đăng nhập bằng `biet.hoang@email.com` | 1. Tìm BOOK003 (Đang mượn).<br>2. Kiểm tra thao tác mượn. | Sách: `BOOK003` | Nút (+) Mượn sách bị ẩn đi. | REQ-04 | EP |
| **TC-15** | Mượn sách thất bại do sách bị "Thất lạc" | Đăng nhập bằng `ba.nguyen@email.com` | 1. Cuộn tìm BOOK020 ("Thất lạc").<br>2. Kiểm tra thao tác mượn. | Sách: `BOOK020` | Nút (+) Mượn sách bị ẩn đi. | REQ-04 | EP |
| **TC-16** | Mượn sách thất bại do tài khoản bị tạm ngưng | Đăng nhập bằng `cu.le@email.com` | 1. Chọn BOOK001 đang "Có sẵn".<br>2. Nhấn "Mượn sách". | Sách: `BOOK001` | Từ chối mượn, thông báo tài khoản bị tạm ngưng. | REQ-04 | EP |
| **TC-17** | Mượn sách thất bại do tài khoản hết hạn | Đăng nhập bằng `binh.pham@email.com` | 1. Chọn BOOK001 đang "Có sẵn".<br>2. Nhấn "Mượn sách". | Sách: `BOOK001` | Từ chối mượn, thông báo tài khoản đã hết hạn. | REQ-04 | EP |
| **TC-18** | Mượn sách thất bại do vượt quá giới hạn 3 cuốn | Đăng nhập `biet.hoang@email.com`, đã mượn đủ 3 sách | 1. Chọn sách "Có sẵn" thứ 4.<br>2. Nhấn "Mượn sách". | Sách thứ 4 bất kỳ | Từ chối mượn, thông báo "Thành viên đã đạt giới hạn 3 sách". | REQ-04 | BVA |
| **TC-19** | Trả sách thành công (đúng hạn) | Đăng nhập bằng `biet.hoang@email.com` | 1. Vào tab Mượn/Trả.<br>2. Tìm phiếu BR003.<br>3. Nhấn "Trả sách". | Phiếu: `BR003` | Phiếu chuyển trạng thái, sách BOOK013 về "Có sẵn". | REQ-05 | EP |
| **TC-20** | Trả sách có cảnh báo quá hạn | Đăng nhập bằng `ba.nguyen@email.com` | 1. Vào tab Mượn/Trả.<br>2. Tìm phiếu BR001 (Quá hạn).<br>3. Nhấn "Trả sách". | Phiếu: `BR001` | Sách BOOK003 về "Có sẵn". Hiển thị cảnh báo trả sách quá hạn. | REQ-05 | BVA |
| **TC-21** | Ẩn nút "Trả sách" với phiếu đã trả | Đăng nhập bằng `ba.nguyen@email.com` | 1. Vào tab Mượn/Trả.<br>2. Xem phiếu BR004 ("Đã trả"). | Phiếu: `BR004` | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả". | REQ-05 | EP |
| **TC-22** | Thủ thư kiểm tra quá hạn hệ thống | Đăng nhập bằng `librarian@library.com` | 1. Vào Tất cả phiếu mượn.<br>2. Nhấn "Kiểm tra sách quá hạn". | (Không có) | Phiếu BR001 tự động cập nhật trạng thái thành "Quá hạn". | REQ-06 | EP |
| **TC-23** | Thêm thành viên mới thành công | Đăng nhập bằng Thủ thư, tab Thành viên | 1. Nhấn Icon (+).<br>2. Nhập thông tin hợp lệ.<br>3. Nhấn "Lưu". | Tên: `Long`, Email: `luc1f3r@library.com`, SĐT: `0987654321` | Lưu thành công, thẻ thành viên mới xuất hiện trong danh sách. | REQ-07 | EP |
| **TC-24** | Thêm thành viên thất bại do bỏ trống thông tin | Đăng nhập bằng Thủ thư, tab Thành viên | 1. Nhấn Icon (+).<br>2. Bỏ trống các ô Họ tên, Email.<br>3. Nhấn "Lưu". | Họ tên: `""`, Email: `""` | Báo lỗi yêu cầu điền đầy đủ thông tin bắt buộc. | REQ-07 | BVA |
| **TC-25** | Thêm thành viên thất bại do email không hợp lệ | Đăng nhập bằng Thủ thư, tab Thành viên | 1. Nhấn Icon (+).<br>2. Nhập email sai định dạng.<br>3. Nhấn "Lưu". | Email: `luc1f3r@domain` | Từ chối lưu, hệ thống báo lỗi định dạng email. | REQ-07 | EP |
| **TC-26** | Thêm thành viên thất bại do trùng email | Đăng nhập bằng Thủ thư, tab Thành viên | 1. Nhấn Icon (+).<br>2. Nhập email đã tồn tại.<br>3. Nhấn "Lưu". | Email: `ba.nguyen@email.com` | Từ chối lưu, thông báo lỗi email đã tồn tại. | REQ-07 | EP |
| **TC-27** | Kiểm tra quyền xem phiếu mượn của Thủ thư | Đăng nhập `librarian@library.com` | 1. Vào tab Mượn/Trả.<br>2. Kiểm tra danh sách. | `librarian@library.com` | Thủ thư thấy tab "Tất cả phiếu mượn" và thấy đủ các phiếu của hệ thống. | REQ-08 | EP |
| **TC-28** | Kiểm tra quyền xem phiếu mượn của Thành viên | Đăng nhập `ba.nguyen@email.com` | 1. Vào tab Mượn/Trả.<br>2. Kiểm tra danh sách. | `ba.nguyen@email.com` | Thành viên chỉ thấy tab "Phiếu mượn của tôi", chỉ hiện BR001 và BR004. | REQ-08 | EP |
| **TC-29** | Tra cứu phiếu mượn bằng mã Thành viên | Đăng nhập `librarian@library.com` | 1. Vào tab Mượn/Trả -> Tra cứu.<br>2. Nhập `MEM003`. | Mã: `MEM003` | Hệ thống lọc và chỉ hiển thị các phiếu mượn của Trần Dựa Dẫm. | REQ-08 | EP |
| **TC-30** | Đăng xuất khỏi hệ thống | Đã đăng nhập vào hệ thống | 1. Nhấn vào icon Đăng xuất ở góc phải trên (AppBar). | (Không có) | Hệ thống xóa phiên bản và điều hướng về màn hình Đăng nhập ban đầu. | REQ-01 | EP |
---

## Tổng hợp

| Nhóm chức năng | Số TC | REQ phủ | Kỹ thuật IDM áp dụng |
|----------------|-------|---------|----------------------|
| Đăng nhập & Đăng xuất | 6 | REQ-01 | Phân lớp tương đương (EP), Phân tích giá trị biên (BVA) |
| Xem, Tìm kiếm và Lọc sách | 7 | REQ-02, REQ-03 | Phân lớp tương đương (EP) |
| Giao dịch Mượn & Trả sách | 9 | REQ-04, REQ-05 | Phân lớp tương đương (EP), Phân tích giá trị biên (BVA) |
| Quản lý của Thủ thư & Tra cứu | 8 | REQ-06, REQ-07, REQ-08 | Phân lớp tương đương (EP), Phân tích giá trị biên (BVA) |
| **Tổng số lượng TC** | **30** | **REQ-01 → REQ-08** | **EP, BVA** |
---
