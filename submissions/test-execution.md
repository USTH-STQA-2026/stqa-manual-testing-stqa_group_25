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
| TC-03 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Mật khẩu không đúng"                    | Trang chủ thông báo "Mật khẩu không đúng"                                                                    | PASS | | |
| TC-04 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Không tìm thấy thành viên"              | Báo lỗi "Không tìm thấy thành viên"                                                                          | PASS | | |
| TC-05 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Vui lòng nhập email và mật khẩu"        | Hệ thống báo "Vui lòng nhập email và mật khẩu"                                                               | PASS | | |
| TC-06 | ĐĂNG XUẤT | Hệ thống xóa phiên bản, điều hướng về màn hình Đăng nhập        | Hệ thống quay trở lại trang đăng nhập                                                                        | PASS | | |
| TC-07 | XEM SÁCH  | Hiện đủ 20 đầu sách. BOOK003 "Đang mượn", BOOK001 "Có sẵn"      | Thấy đủ 20 sách, BOOK003 trong trạng thái "Đang mượn",BOOK001 có sẵn                                         | PASS | | |
| TC-09 | TÌM KIẾM  | Hiện sách BOOK001 (Không phân biệt hoa/thường)                  | Hiển thị sách BOOK001                                                                                        | PASS | | |
| TC-10 | TÌM KIẾM  | Hệ thống tự cắt khoảng trắng (trim) và tìm ra sách BOOK001      | Hệ thống không tìm thấy sách                                                                                 | FAIL | |X|
| TC-11 | TÌM KIẾM  | Hiển thị thông báo "Không tìm thấy sách"                        | Hệ thống thông báo không tìm thấy sách                                                                       | PASS | | |
| TC-12 | LỌC SÁCH  | Hiển thị danh sách các sách thuộc nhóm Công nghệ                | Hiển thị danh sách thuộc nhóm công nghệ                                                                      | PASS | | |
| TC-13 | LỌC SÁCH  | Hiển thị danh sách các sách thuộc nhóm Công nghệ                | Hiển thị danh sách thuộc nhóm công nghệ                                                                      | PASS | | |
| TC-14 | LỌC SÁCH  | Hiển thị "Không tìm thấy sách nào" do xung đột điều kiện        | Tìm thấy sách thuộc nhóm kinh tế                                                                             | FAIL | |X|
| TC-15 | MƯỢN SÁCH | Sách thành "Đang mượn". Hệ thống sinh phiếu mượn mới            | Trạng thái sách chuyển thành "Đang mượn", hệ thống nhận phiếu mượn mới                                       | PASS | | |
| TC-16 | MƯỢN SÁCH | Nút (+) Mượn sách bị ẩn đi                                      | Nút (+) Mượn sách bị ẩn đi                                                                                   | PASS | | |
| TC-17 | MƯỢN SÁCH | Nút (+) Mượn sách bị ẩn đi                                      | Nút (+) Mượn sách bị ẩn đi                                                                                   | PASS | | |
| TC-18 | MƯỢN SÁCH | Từ chối mượn, thông báo tài khoản bị tạm ngưng                  | Từ chối mượn và thông báo "tài khoản tạm ngưng"                                                              | PASS | | |
| TC-19 | MƯỢN SÁCH | Từ chối mượn, thông báo tài khoản đã hết hạn                    | Hệ thống thông báo "tài khoản tạm ngưng"                                                                     | PASS | | |
| TC-20 | MƯỢN SÁCH | Từ chối mượn, thông báo "Thành viên đã đạt giới hạn 3 sách"     | Hệ thống thông báo "Giới hạn 3 sách"                                                                         | PASS | | |
| TC-21 | TRẢ SÁCH  | Sách BOOK003 về "Có sẵn". Hiển thị cảnh báo quá hạn             | Hệ thống báo trả sách thành công                                                                             | FAIL | |X|
| TC-22 | TRẢ SÁCH  | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả"     | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả"                                                  | PASS | | |
| TC-23 | THỦ THƯ   | Phiếu BR001 và BR003 tự động cập nhật thành "Quá hạn"           | Phiếu BR001 và BR003 cập nhật quá hạn                                                                        | PASS | | |
| TC-24 | QUẢN LÝ USER | Lưu thành công, thẻ thành viên mới xuất hiện trong danh sách | Hệ thống báo "Email không hợp lệ"                                                                            | FAIL | |X|
| TC-25 | QUẢN LÝ USER | Báo lỗi yêu cầu điền đầy đủ thông tin bắt buộc               | Hệ thống yêu cầu điền đủ thông tin                                                                           | PASS | | |
| TC-26 | QUẢN LÝ USER | Từ chối lưu, hệ thống báo lỗi định dạng email                | Thêm thành viên thành công                                                                                   | FAIL | |X|
| TC-27 | QUẢN LÝ USER | Từ chối lưu, thông báo lỗi email đã tồn tại                  | Thông báo lỗi email đã tồn tại                                                                               | PASS | | |
| TC-28 | TRA CỨU | Thủ thư thấy tab "Tất cả phiếu mượn" và thấy đủ các phiếu         | Thấy tất cả phiếu mượn" và thấy đủ các phiếu của hệ thống.                                                   | PASS | | |
| TC-29 | TRA CỨU | Thành viên chỉ thấy tab "Phiếu mượn của tôi" (BR001, BR004)       | Thành viên chỉ thấy tab "Phiếu mượn của tôi" và chỉ hiện BR001 và BR004.                                     | PASS | | |
| TC-30 | TRA CỨU | Hệ thống lọc và chỉ hiển thị các phiếu mượn của MEM003            | Hệ thống lọc và chỉ hiển thị các phiếu mượn của Trần Dựa Dẫm.                                                | PASS | | |

---

## Tổng hợp kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `30` |
| Pass | `25` |
| Fail | `5` |
| Blocked | `0` |
| Not Run | `0` |
| **Tỷ lệ Pass** | `83.33%` |

### Kết quả theo nhóm chức năng

| Nhóm | Tổng TC | Pass | Fail | Tỷ lệ Pass |
|------|---------|------|------|------------|
| Đăng nhập & Đăng xuất | 6 | 6 | 0 | 100.00% |
| Xem, Tìm kiếm & Lọc sách | 8 | 6 | 2 | 75.00% |
| Giao dịch Mượn & Trả sách | 8 | 7 | 1 | 87.50% |
| Thủ thư, Quản lý & Tra cứu | 8 | 6 | 2 | 75.00% |
