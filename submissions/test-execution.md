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
| TC-01 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thành viên" | Hệ thống chuyển hướng đến trang chủ. AppBar hiển thị vai trò "Thành viên". | PASS | | |
| TC-02 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thủ thư" | Hệ thống chuyển hướng đến trang chủ. AppBar hiển thị vai trò "Thủ thư". Có thêm tab "Thành viên". | PASS | | |
| TC-03 | ĐĂNG NHẬP | Báo lỗi "Mật khẩu không đúng" | Hệ thống không chuyển trang. Hiển thị thông báo "Mật khẩu không đúng". | PASS | | |
| TC-04 | ĐĂNG NHẬP | Báo lỗi "Không tìm thấy thành viên" | Hệ thống không chuyển trang. Hiển thị thông báo "Không tìm thấy thành viên". | PASS | | |
| TC-05 | ĐĂNG NHẬP | Báo lỗi "Vui lòng nhập email và mật khẩu" | Hệ thống không chuyển trang. Hiển thị thông báo "Vui lòng nhập email và mật khẩu". | PASS | | |
| TC-06 | XEM SÁCH | Hiện 20 sách, đúng trạng thái mượn/có sẵn | Hiện 20 sách, đúng trạng thái mượn/có sẵn | PASS | | |
| TC-07 | TÌM KIẾM | Hiện sách "Lập trình Flutter cơ bản" | Hiển thị sách BOOK001 (Lập trình Flutter cơ bản) | PASS | | |
| TC-08 | TÌM KIẾM | Hiện BOOK001 và BOOK009 | Hiển thị BOOK001 và BOOK009 | PASS | | |
| TC-09 | TÌM KIẾM | Báo "Không tìm thấy sách" | Hiển thị thông báo "Không tìm thấy sách" | PASS | | |
| TC-10 | MƯỢN SÁCH | Sách đổi sang "Đã mượn", sinh phiếu mới | Trạng thái sách chuyển thành "Đang mượn". Hệ thống sinh phiếu mượn mới. | PASS | | |
| TC-11 | MƯỢN SÁCH | Nút Mượn bị ẩn/vô hiệu hóa ở BOOK003 | 	Nút "Mượn sách" bị ẩn đi. | PASS | | |
| TC-12 | MƯỢN SÁCH | Từ chối, báo tài khoản bị tạm ngưng | Thành viên đã hết hạn. Không thể mượn sách | FAIL | | |
| TC-13 | MƯỢN SÁCH | Từ chối, báo tài khoản đã hết hạn | Thành viên đã hết hạn. Không thể mượn sách | PASS | | |
| TC-14 | MƯỢN SÁCH | Báo vượt giới hạn 3 sách | Từ chối mượn, thông báo "Đã đạt giới hạn mượn tối đa (3 sách)". | PASS | | |
| TC-15 | TRẢ SÁCH | Sách thành "Có sẵn", không có cảnh báo | Sách BOOK013 chuyển về trạng thái "Có sẵn". | PASS | | |
| TC-16 | TRẢ SÁCH | Sách thành "Có sẵn", hiển thị cảnh báo quá hạn | Sách BOOK003 chuyển về "Có sẵn". Không hiển thị cảnh báo quá hạn | FAIL | | |
| TC-17 | THỦ THƯ | Phiếu BR001 tự động đổi thành "Quá hạn" | Phiếu BR001 tự động đổi thành "Quá hạn" | PASS | | |
| TC-18 | QUẢN LÝ USER | Lưu thành công, tạo thành viên mới | Tạo tài khoản không thành công. Báo "Email không hợp lệ | FAIL | | |
| TC-19 | QUẢN LÝ USER | Báo lỗi định dạng email không hợp lệ | Thêm thành viên thành công | FAIL | | |
| TC-20 | QUẢN LÝ USER | Báo lỗi email đã tồn tại | Báo lỗi "Email không hợp lệ | PASS | | |
| TC-21 | TRA CỨU | Thủ thư thấy 5 phiếu, MEM002 thấy 2 phiếu | Thủ thư thấy 5 phiếu, MEM002 thấy 2 phiếu | PASS | | |
---

## Tổng hợp kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `21` |
| Pass | `17` |
| Fail | `4` |
| Blocked | `0` |
| Not Run | `0` |
| **Tỷ lệ Pass** | `80.95%` |

### Kết quả theo nhóm chức năng

| Nhóm | Tổng TC | Pass | Fail | Tỷ lệ Pass |
|------|---------|------|------|------------|
| ĐĂNG NHẬP | 5 | 5 | 0 | 100% |
| XEM & TÌM KIẾM SÁCH | 4 | 4 | 0 | 100% |
| MƯỢN & TRẢ SÁCH | 7 | 5 | 2 | 71.43% |
| THỦ THƯ & QUẢN LÝ | 5 | 3 | 2 | 60% |
