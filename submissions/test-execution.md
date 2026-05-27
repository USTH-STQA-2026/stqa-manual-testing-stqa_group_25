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

| Mã TC | Nhóm chức năng | Kết quả mong đợi (tóm tắt)                    | Kết quả thực tế                                                                                | Kết luận | Minh chứng | Bug |
|-------|--------------- |---------------------------                    |-----------------                                                                               |--------- |----------- |---- | 
| TC-01 | LOGIN          | Go to home page, AppBar displays "Thủ thư"    | System redirects to home page. AppBar shows name and role "Thủ thư". "Thành viên" tab appears  | PASS     | | |
| TC-02 | LOGIN          | Go to home page, AppBar displays "Thành viên" | System redirects to home page. AppBar shows "Ba Nguyễn — Thành viên". "Thành viên" tab does not appear | PASS |  |  |
| TC-03 | LOGIN          | "Không tìm thấy thành viên"                   | System does not redirect. Displays message "Không tìm thấy thành viên"                         | PASS |  |  |
| TC-04 | LOGIN          | "Mật khẩu không đúng"                         | System does not redirect. Displays message "Mật khẩu không đúng"                               | PASS |  |  |
| TC-05 | LOGIN          | "Vui lòng nhập email và mật khẩu"             | System does not redirect. Displays message "Mật khẩu không đúng"                               | PASS |  |  |

---

## Tổng hợp kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `<!-- số -->` |
| Pass | `<!-- số -->` |
| Fail | `<!-- số -->` |
| Blocked | `<!-- số -->` |
| Not Run | `<!-- số -->` |
| **Tỷ lệ Pass** | `<!-- xx% -->` |

### Kết quả theo nhóm chức năng

| Nhóm | Tổng TC | Pass | Fail | Tỷ lệ Pass |
|------|---------|------|------|------------|
| | | | | |
