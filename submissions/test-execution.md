# Test Execution — Kết quả thực thi kiểm thử

> **Hướng dẫn**: Chạy từng TC trên hệ thống https://stqa.rbc.vn, ghi lại kết quả thực tế.
> Kết luận: **Pass** (kết quả đúng), **Fail** (kết quả sai → tạo bug report), **Blocked** (không thực hiện được vì lỗi khác chặn), **Not Run** (chưa chạy).

| Thông tin | |
|---|---|
| **Nhóm** | `Group 25` |
| **Ngày thực thi** | `<!-- DD/MM/YYYY -->` |
| **Trình duyệt** | Chrome `<!-- version -->` |
| **Hệ điều hành** | `Windows11` |

---

## Kết quả chi tiết

| Mã TC | Nhóm chức năng | Kết quả mong đợi (tóm tắt) | Kết quả thực tế | Kết luận | Minh chứng | Bug |
|-------|--------------- |--------------------------- |-----------------|----------|------------|-----|
| TC-01 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thành viên" | Chuyển trang chủ, AppBar hiện vai trò "Thành viên" | PASS | | |
| TC-02 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thủ thư" | Chuyển trang chủ, AppBar hiện vai trò "Thủ thư" | PASS | | |
| TC-03 | ĐĂNG NHẬP | Báo lỗi "Mật khẩu không đúng" | Báo lỗi "Mật khẩu không đúng" | PASS | | |
| TC-04 | ĐĂNG NHẬP | Báo lỗi "Không tìm thấy thành viên" | Báo lỗi "Không tìm thấy thành viên" | PASS | | |
| TC-05 | ĐĂNG NHẬP | Báo lỗi "Vui lòng nhập email và mật khẩu" | Báo lỗi "Vui lòng nhập email và mật khẩu" | PASS | | |
| TC-06 | XEM SÁCH | Hiện 20 sách, đúng trạng thái mượn/có sẵn | Hiện 20 sách, đúng trạng thái mượn/có sẵn | PASS | | |
| TC-07 | TÌM KIẾM | Hiển thị sách BOOK001 (Lập trình Flutter cơ bản) và sách BOOK009 (Nhập môn lập trình Python) | Hiển thị sách BOOK001 và sách BOOK009 | PASS | | |
| TC-08 | TÌM KIẾM | Hiện sách "Lập trình Flutter cơ bản"  | Hiện sách "Lập trình Flutter cơ bản" | PASS | | |
| TC-09 | TÌM KIẾM | Báo "Không tìm thấy sách" | Báo "Không tìm thấy sách" | PASS | | |
| TC-10 | TÌM KIẾM | Hiển thị sách thể loại công nghệ | Hiển thị sách thể loại công nghệ | PASS | | |
| TC-11 | TÌM KIẾM | Hiển thị sách thể loại công nghệ | Báo không tìm thấy sách nào
| FAIL | | X |
| TC-12 | TÌM KIẾM | Báo "Không tìm thấy sách nào" do xung đột lọc | Hiển thị "Không tìm thấy sách" | PASS | | |
| TC-13 | MƯỢN SÁCH | Sách đổi sang "Đang mượn", sinh phiếu mới | Trạng thái sách chuyển thành "Đang mượn". Hệ thống sinh phiếu mượn mới. | PASS | | |
| TC-14 | MƯỢN SÁCH | Nút Mượn bị ẩn/vô hiệu hóa ở BOOK003 | Nút (+) Mượn sách bị ẩn đi | PASS | | |
| TC-15 | MƯỢN SÁCH | Nút Mượn bị ẩn ở sách "Thất lạc" | Nút (+) Mượn sách bị ẩn đi. | PASS | | |
| TC-16 | MƯỢN SÁCH | Từ chối, báo tài khoản bị tạm ngưng | Từ chối mượn, thông báo tài khoản đã hết hạn. | FAIL | | X |
| TC-17 | MƯỢN SÁCH | Từ chối, báo tài khoản đã hết hạn | 	Từ chối mượn, thông báo tài khoản đã hết hạn. | PASS | | |
| TC-18 | MƯỢN SÁCH | Báo vượt giới hạn 3 sách | Từ chối mượn, thông báo "Thành viên đã đạt giới hạn tối đa (3 sách)". | PASS | | |
| TC-19 | TRẢ SÁCH | Sách thành "Có sẵn", cảnh báo quá hạn | Phiếu chuyển trạng thái, sách BOOK013 về "Có sẵn" | FAIL | | x |
| TC-20 | TRẢ SÁCH | Sách thành "Có sẵn", cảnh báo quá hạn | Phiếu chuyển trạng thái, sách BOOK003 về "Có sẵn" | FAIL | | X |
| TC-21 | TRẢ SÁCH | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả". | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả". | PASS | | |
| TC-22 | THỦ THƯ | Phiếu BR001 và BR003 tự động đổi thành "Quá hạn" | Phiếu BR001 và BR003 tự động đổi thành "Quá hạn" | PASS | | |
| TC-23 | QUẢN LÝ USER | Lưu thành công, tạo thành viên mới | Thêm không thành công, báo "Email không hợp lệ" | FAIL | | X |
| TC-24 | QUẢN LÝ USER | Báo lỗi yêu cầu điền đầy đủ thông tin | Báo lỗi yêu cầu điền đầy đủ thông tin | PASS | | |
| TC-25 | QUẢN LÝ USER | Báo lỗi định dạng email không hợp lệ | Thêm thành viên thành công | FAIL | | X |
| TC-26 | QUẢN LÝ USER | Báo lỗi email đã tồn tại | Thêm không thành công, báo "Email không hợp lệ" | PASS | | |
| TC-27 | TRA CỨU | Thủ thư thấy tab Tất cả phiếu mượn | Thủ thư thấy tab Tất cả phiếu mượn | PASS | | |
| TC-28 | TRA CỨU | Thành viên chỉ thấy Phiếu mượn của tôi | Thành viên chỉ thấy Phiếu mượn của tôi | PASS | | |
| TC-29 | TRA CỨU | Lọc đúng phiếu của MEM003 | Lọc đúng phiếu của MEM003 | PASS | | |
| TC-30 | ĐĂNG XUẤT | Trở về màn hình Đăng nhập | Trở về màn hình Đăng nhập | PASS | | |

---

## Tổng hợp kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `30` |
| Pass | `24` |
| Fail | `6` |
| Blocked | `0` |
| Not Run | `0` |
| **Tỷ lệ Pass** | `80.00%` |

### Kết quả theo nhóm chức năng

| Nhóm | Tổng TC | Pass | Fail | Tỷ lệ Pass |
|------|---------|------|------|------------|
| Đăng nhập & Đăng xuất | 6 | 6 | 0 | 100% |
| Xem, Tìm kiếm & Lọc sách | 7 | 6 | 1 | 85.71% |
| Giao dịch Mượn & Trả sách | 9 | 6 | 3 | 66.67% |
| Thủ thư, Quản lý & Tra cứu | 8 | 6 | 2 | 75.00% |
