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
| TC-03 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Mật khẩu không đúng" | ... | ... | | |
| TC-04 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Không tìm thấy thành viên" | ... | ... | | |
| TC-05 | ĐĂNG NHẬP | Hiển thị thông báo lỗi "Vui lòng nhập email và mật khẩu" | ... | ... | | |
| TC-06 | ĐĂNG XUẤT | Hệ thống xóa phiên bản, điều hướng về màn hình Đăng nhập | ... | ... | | |
| TC-07 | XEM SÁCH | Hiện đủ 20 đầu sách. BOOK003 "Đang mượn", BOOK001 "Có sẵn" | ... | ... | | |
| TC-08 | TÌM KIẾM | Hiển thị sách BOOK001 và sách BOOK009 | ... | ... | | |
| TC-09 | TÌM KIẾM | Hiện sách BOOK001 (Không phân biệt hoa/thường) | ... | ... | | |
| TC-10 | TÌM KIẾM | Hệ thống tự cắt khoảng trắng (trim) và tìm ra sách BOOK001 | ... | ... | | |
| TC-11 | TÌM KIẾM | Hiển thị thông báo "Không tìm thấy sách" | ... | ... | | |
| TC-12 | LỌC SÁCH | Hiển thị danh sách các sách thuộc nhóm Công nghệ | ... | ... | | |
| TC-13 | LỌC SÁCH | Hiển thị danh sách các sách thuộc nhóm Công nghệ | ... | ... | | |
| TC-14 | LỌC SÁCH | Hiển thị "Không tìm thấy sách nào" do xung đột điều kiện | ... | ... | | |
| TC-15 | MƯỢN SÁCH | Sách thành "Đang mượn". Hệ thống sinh phiếu mượn mới | ... | ... | | |
| TC-16 | MƯỢN SÁCH | Nút (+) Mượn sách bị ẩn đi | ... | ... | | |
| TC-17 | MƯỢN SÁCH | Nút (+) Mượn sách bị ẩn đi | ... | ... | | |
| TC-18 | MƯỢN SÁCH | Từ chối mượn, thông báo tài khoản bị tạm ngưng | ... | ... | | |
| TC-19 | MƯỢN SÁCH | Từ chối mượn, thông báo tài khoản đã hết hạn | ... | ... | | |
| TC-20 | MƯỢN SÁCH | Từ chối mượn, thông báo "Thành viên đã đạt giới hạn 3 sách" | ... | ... | | |
| TC-21 | TRẢ SÁCH | Sách BOOK003 về "Có sẵn". Hiển thị cảnh báo quá hạn | ... | ... | | |
| TC-22 | TRẢ SÁCH | Nút "Trả sách" màu xanh không hiển thị ở các phiếu "Đã trả" | ... | ... | | |
| TC-23 | THỦ THƯ | Phiếu BR001 và BR003 tự động cập nhật thành "Quá hạn" | ... | ... | | |
| TC-24 | QUẢN LÝ USER | Lưu thành công, thẻ thành viên mới xuất hiện trong danh sách | ... | ... | | |
| TC-25 | QUẢN LÝ USER | Báo lỗi yêu cầu điền đầy đủ thông tin bắt buộc | ... | ... | | |
| TC-26 | QUẢN LÝ USER | Từ chối lưu, hệ thống báo lỗi định dạng email | ... | ... | | |
| TC-27 | QUẢN LÝ USER | Từ chối lưu, thông báo lỗi email đã tồn tại | ... | ... | | |
| TC-28 | TRA CỨU | Thủ thư thấy tab "Tất cả phiếu mượn" và thấy đủ các phiếu | ... | ... | | |
| TC-29 | TRA CỨU | Thành viên chỉ thấy tab "Phiếu mượn của tôi" (BR001, BR004) | ... | ... | | |
| TC-30 | TRA CỨU | Hệ thống lọc và chỉ hiển thị các phiếu mượn của MEM003 | ... | ... | | |

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
| Xem, Tìm kiếm & Lọc sách | 8 | ... | ... | ...% |
| Giao dịch Mượn & Trả sách | 8 | ... | ... | ...% |
| Thủ thư, Quản lý & Tra cứu | 8 | ... | ... | ...% |
