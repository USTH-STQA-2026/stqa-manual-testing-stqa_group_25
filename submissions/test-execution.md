| Thông tin | |
|---|---|
| **Nhóm** | `Group 25` |
| **Ngày thực thi** | `<!-- 8/6/2026 -->` |
| **Trình duyệt** | Chrome `<!-- version -->` |
| **Hệ điều hành** | `Windows11` |

---

## Kết quả chi tiết

| Mã TC | Nhóm chức năng | Kết quả mong đợi (tóm tắt) | Kết quả thực tế | Kết luận | Minh chứng | Bug |
|-------|--------------- |--------------------------- |-----------------|----------|------------|-----|
| TC-01 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thành viên"              | Đăng nhập, hiện trang chủ, hiện vai trò thành viên                                                           | PASS | | |
| TC-02 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thủ thư"                 | Đăng nhập, hiện trang chủ, hiện vai trò thủ thư                                                              | PASS | | |
| TC-03 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Mật khẩu không đúng"                    | Nhập sai mật khẩu, trang chủ thông báo "Mật khẩu không đúng"                                                 | PASS | | |
| TC-04 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Không tìm thấy thành viên"              | Đăng nhập, nhập tài khoản mật khẩu, báo lỗi"Không tìm thấy thành viên"                                       | PASS | | |
| TC-05 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Vui lòng nhập email và mật khẩu"        | Đăng nhập, bỏ trống email hoặc mật khẩu, hệ thống báo"Vui lòng nhập email và mật khẩu"                       | PASS | | |
| TC-06 | ĐĂNG XUẤT | Hệ thống xóa phiên bản, điều hướng về màn hình Đăng nhập        | Đăng xuất, hệ thống quay trở lại trang đăng nhập                                                             | PASS | | |
| TC-07 | XEM SÁCH  | Hiện đủ 20 đầu sách. BOOK003 "Đang mượn", BOOK001 "Có sẵn"      | Đăng nhập, thấy đủ 20 sách, BOOK003 trong trạng thái"Đang mượn",BOOK001 có sẵn                               | PASS | | |
| TC-09 | TÌM KIẾM  | Hiện sách BOOK001 (Không phân biệt hoa/thường)                  | Nhập từ khóa "Flutter", hiển thị sách BOOK001                                                                | PASS | | |
| TC-10 | TÌM KIẾM  | Hệ thống tự cắt khoảng trắng (trim) và tìm ra sách BOOK001      | Nhập Từ khóa: "Flutter    ", hệ thống không tìm thấy sách, không tự cắt khoảng trắng                         | FAIL | |x|
| TC-11 | TÌM KIẾM  | Hiển thị thông báo "Không tìm thấy sách"                        | Nhập từ khóa "Sách Nấu Ăn", hệ thống thông báo không tìm thấy sách                                           | PASS | | |
| TC-12 | LỌC SÁCH  | Hiển thị danh sách các sách thuộc nhóm Công nghệ                | Lọc từ khóa "Công nghệ", hiển thị danh sách thuộc nhóm công nghệ                                             | PASS | | |
| TC-13 | LỌC SÁCH  | Hiển thị danh sách các sách thuộc nhóm Công nghệ                | Lọc từ khóa "công nghệ", , hiển thị danh sách thuộc nhóm công nghệ                                           | PASS | | |
| TC-14 | LỌC SÁCH  | Hiển thị "Không tìm thấy sách nào" do xung đột điều kiện        | Tìm từ khóa "Flutter", Lọc: "Kinh tế", vẫn tìm thấy sách về kinh tế                                          | FAIL | |x|
| TC-15 | MƯỢN SÁCH | Sách thành "Đang mượn". Hệ thống sinh phiếu mượn mới            | Chọn mượn sách BOOK001,Trạng thái sách chuyển thành "Đang mượn", hệ thống nhận phiếu mượn mới                | PASS | | |
| TC-16 | MƯỢN SÁCH | Nút (+) Mượn sách bị ẩn đi                                      | Tìm BOOK003, nút (+) Mượn sách bị ẩn đi                                                                      | PASS | | |
| TC-17 | MƯỢN SÁCH | Nút (+) Mượn sách bị ẩn đi                                      | Tìm BOOK020 "Thất lạc", nút (+) Mượn sách bị ẩn đi                                                           | PASS | | |
| TC-18 | MƯỢN SÁCH | Từ chối mượn, thông báo tài khoản bị tạm ngưng                  | Tìm sách BOOK001 từ chối mượn và thông báo "tài khoản tạm ngưng"                                             | PASS | | |
| TC-19 | MƯỢN SÁCH | Từ chối mượn, thông báo tài khoản đã hết hạn                    | Chọn BOOK001 và nhấn "Mượn sách", hệ thống thông báo "tài khoản tạm ngưng"                                   | PASS | | |
| TC-20 | MƯỢN SÁCH | Từ chối mượn, thông báo "Thành viên đã đạt giới hạn 3 sách"     | Mượn 4 sách, đến 3 sách hệ thống thông báo "Giới hạn 3 sách"                                                 | PASS | | |
| TC-21 | TRẢ SÁCH  | Sách BOOK003 về "Có sẵn". Hiển thị cảnh báo quá hạn             | Vào "Mượn/trả", tìm phiếu BR001 và nhấn "Trả sách", hệ thống báo trả sách thành công                         | FAIL | |x|
| TC-22 | TRẢ SÁCH  | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả"     | Vào tab Mượn/Trả và xem phiếu BR004 ("Đã trả"),nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả"   | PASS | | |
| TC-23 | THỦ THƯ   | Phiếu BR001 và BR003 tự động cập nhật thành "Quá hạn"           | Vào Tất cả phiếu mượn và kiểm tra sách quá hạn, phiếu BR001 và BR003 cập nhật quá hạn                        | PASS | | |
| TC-24 | QUẢN LÝ USER | Lưu thành công, thẻ thành viên mới xuất hiện trong danh sách | Nhập họ tên email và số điện thoại thẻ thành viên, hệ thống báo "Email không hợp lệ"                         | FAIL | |x|
| TC-25 | QUẢN LÝ USER | Báo lỗi yêu cầu điền đầy đủ thông tin bắt buộc               | Nhấn thêm thành viên, bỏ trống email và họ tên, hệ thống yêu cầu điền đủ thông tin                           | PASS | | |
| TC-26 | QUẢN LÝ USER | Từ chối lưu, hệ thống báo lỗi định dạng email                | Thêm thành viên, nhập email, hệ thống báo "Họ tên không được để trống"                                       | FAIL | |x|
| TC-27 | QUẢN LÝ USER | Từ chối lưu, thông báo lỗi email đã tồn tại                  | Thêm thành viên, nhập email, hệ thống báo "Họ tên không được để trống"                                       | FAIL | |x|
| TC-28 | TRA CỨU | Thủ thư thấy tab "Tất cả phiếu mượn" và thấy đủ các phiếu         | Nhấn Mượn/Trả và kiểm tra danh sách, thấy tất cả phiếu mượn" và thấy đủ các phiếu của hệ thống.              | PASS | | |
| TC-29 | TRA CỨU | Thành viên chỉ thấy tab "Phiếu mượn của tôi" (BR001, BR004)       | Nhấn Mượn/Trả và kiểm tra danh sách,thành viên chỉ thấy tab "Phiếu mượn của tôi" và chỉ hiện BR001 và BR004. | PASS | | |
| TC-30 | TRA CỨU | Hệ thống lọc và chỉ hiển thị các phiếu mượn của MEM003            | Nhấn Mượn/Trả, nhập mã MEM003, hệ thống lọc và chỉ hiển thị các phiếu mượn của Trần Dựa Dẫm.                 | PASS | | |

---

## Tổng hợp kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `30` |
| Pass | `24` |
| Fail | `6` |
| Blocked | `0` |
| Not Run | `0` |
| **Tỷ lệ Pass** | `80%` |

### Kết quả theo nhóm chức năng

| Nhóm | Tổng TC | Pass | Fail | Tỷ lệ Pass |
|------|---------|------|------|------------|
| Đăng nhập & Đăng xuất | 6 | 6 | 0 | 100% |
| Xem, Tìm kiếm & Lọc sách | 8 | 6 | 2 | 75% |
| Giao dịch Mượn & Trả sách | 8 | 7 | 1 | 87.5% |
| Thủ thư, Quản lý & Tra cứu | 8 | 5 | 3 | 62.5% |
