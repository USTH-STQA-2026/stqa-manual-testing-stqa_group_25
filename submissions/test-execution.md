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
| TC-01 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thành viên" | ... | ... | | |
| TC-02 | ĐĂNG NHẬP | Chuyển trang chủ, AppBar hiện vai trò "Thủ thư" | ... | ... | | |
| TC-03 | ĐĂNG NHẬP | Báo lỗi "Mật khẩu không đúng" | ... | ... | | |
| TC-04 | ĐĂNG NHẬP | Báo lỗi "Không tìm thấy thành viên" | ... | ... | | |
| TC-05 | ĐĂNG NHẬP | Báo lỗi "Vui lòng nhập email và mật khẩu" | ... | ... | | |
| TC-06 | XEM SÁCH | Hiện 20 sách, đúng trạng thái mượn/có sẵn | ... | ... | | |
| TC-07 | TÌM KIẾM | Hiện sách "Lập trình Flutter cơ bản" | ... | ... | | |
| TC-08 | TÌM KIẾM | Hiện sách "Lập trình Flutter cơ bản" (từ khóa IN HOA) | ... | ... | | |
| TC-09 | TÌM KIẾM | Báo "Không tìm thấy sách" | ... | ... | | |
| TC-10 | TÌM KIẾM | Lọc theo "Công nghệ" hiển thị sách | ... | ... | | |
| TC-11 | TÌM KIẾM | Lọc theo "công nghệ" (chữ thường) hiển thị sách | ... | ... | | |
| TC-12 | TÌM KIẾM | Báo "Không tìm thấy sách" do xung đột lọc | ... | ... | | |
| TC-13 | MƯỢN SÁCH | Sách đổi sang "Đang mượn", sinh phiếu mới | ... | ... | | |
| TC-14 | MƯỢN SÁCH | Nút Mượn bị ẩn/vô hiệu hóa ở BOOK003 | ... | ... | | |
| TC-15 | MƯỢN SÁCH | Nút Mượn bị ẩn ở sách "Thất lạc" | ... | ... | | |
| TC-16 | MƯỢN SÁCH | Từ chối, báo tài khoản bị tạm ngưng | ... | ... | | |
| TC-17 | MƯỢN SÁCH | Từ chối, báo tài khoản đã hết hạn | ... | ... | | |
| TC-18 | MƯỢN SÁCH | Báo vượt giới hạn 3 sách | ... | ... | | |
| TC-19 | TRẢ SÁCH | Sách thành "Có sẵn", không có cảnh báo | ... | ... | | |
| TC-20 | TRẢ SÁCH | Sách thành "Có sẵn", hiển thị cảnh báo quá hạn | ... | ... | | |
| TC-21 | TRẢ SÁCH | Ẩn nút "Trả sách" với phiếu "Đã trả" | ... | ... | | |
| TC-22 | THỦ THƯ | Phiếu BR001 tự động đổi thành "Quá hạn" | ... | ... | | |
| TC-23 | QUẢN LÝ USER | Lưu thành công, tạo thành viên mới | ... | ... | | |
| TC-24 | QUẢN LÝ USER | Báo lỗi yêu cầu điền đầy đủ thông tin | ... | ... | | |
| TC-25 | QUẢN LÝ USER | Báo lỗi định dạng email không hợp lệ | ... | ... | | |
| TC-26 | QUẢN LÝ USER | Báo lỗi email đã tồn tại | ... | ... | | |
| TC-27 | TRA CỨU | Thủ thư thấy tab Tất cả phiếu mượn | ... | ... | | |
| TC-28 | TRA CỨU | Thành viên chỉ thấy Phiếu mượn của tôi | ... | ... | | |
| TC-29 | TRA CỨU | Lọc đúng phiếu của MEM003 | ... | ... | | |
| TC-30 | ĐĂNG XUẤT | Trở về màn hình Đăng nhập | ... | ... | | |

---

## Tổng hợp kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `30` |
| Pass | `...` |
| Fail | `...` |
| Blocked | `...` |
| Not Run | `...` |
| **Tỷ lệ Pass** | `...%` |

### Kết quả theo nhóm chức năng

| Nhóm | Tổng TC | Pass | Fail | Tỷ lệ Pass |
|------|---------|------|------|------------|
| Đăng nhập & Đăng xuất | 6 | ... | ... | ...% |
| Xem, Tìm kiếm & Lọc sách | 7 | ... | ... | ...% |
| Giao dịch Mượn & Trả sách | 9 | ... | ... | ...% |
| Thủ thư, Quản lý & Tra cứu | 8 | ... | ... | ...% |
