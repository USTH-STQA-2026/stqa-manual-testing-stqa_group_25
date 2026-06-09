# Test Summary — Báo cáo tổng hợp kiểm thử

---

## 1. Thông tin nhóm

| Mục | Thông tin |
|-----|----------|
| **Nhóm** | `Group 25` |
| **Ngày báo cáo** | `08/06/2026` |
| **Hệ thống kiểm thử** | https://stqa.rbc.vn — v1.0 |

---

## 2. Tổng quan kết quả

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số test case | `30` |
| Pass | `25` |
| Fail | `5` |
| Blocked | `0` |
| Not Run | `0` |
| **Tỷ lệ Pass** | `83.33%` |
| **Số bug phát hiện** | `5` |

### Phân bổ theo nhóm chức năng

| Nhóm chức năng | TC | Pass | Fail | Bug | Đánh giá |
|---------------|-----|------|------|-----|---------|
| Đăng nhập & Đăng xuất | 6 | 6 | 0 | 0 | **Tốt**. Luồng xác thực hoạt động ổn định, bắt lỗi rỗng/sai pass chính xác. |
| Xem, Tìm kiếm & Lọc sách | 8 | 6 | 2 | 2 | **Cần cải thiện**. Lỗi thuật toán xử lý chuỗi (chưa cắt khoảng trắng) và xung đột logic bộ lọc. |
| Giao dịch Mượn & Trả sách | 8 | 7 | 1 | 1 | **Khá tốt**. Core logic mượn sách ổn định, chặn giới hạn sách đúng. Tuy nhiên lỗi thiếu cảnh báo quá hạn khi trả sách khá rủi ro. |
| Thủ thư, Quản lý & Tra cứu | 8 | 6 | 2 | 2 | **Nghiêm trọng**. Tính năng Thêm thành viên mới bị tê liệt do sai Regex validate Email. |

### Phân bổ bug theo mức độ

| Mức độ | Số lượng | Bug IDs |
|--------|---------|---------|
| High | 3 | BUG-03, BUG-04, BUG-05 |
| Medium | 2 | BUG-01, BUG-02 |
| Low | 0 | |

---

## 3. Kỹ thuật thiết kế đã sử dụng

| Kỹ thuật | Áp dụng cho REQ nào? | Số TC sử dụng | Giải thích cách áp dụng |
|----------|---------------------|---------------|------------------------|
| Phân lớp tương đương (EP) | Toàn bộ hệ thống (REQ-01 → REQ-08) | 26 | Chia đầu vào thành các nhóm hợp lệ (VD: email đúng định dạng) và không hợp lệ (VD: sai pass, email thiếu `@`) để tối ưu hóa số lượng TC mà vẫn đảm bảo độ phủ. |
| Phân tích giá trị biên (BVA) | REQ-01, REQ-03, REQ-04, REQ-07 | 4 | Tập trung vào các điểm cận biên dễ gây lỗi như: Bỏ trống hoàn toàn ô nhập (`""`), mượn đúng giới hạn 3 cuốn, và có khoảng trắng ở biên từ khóa tìm kiếm. |

---

## 4. Phân tích chất lượng phần mềm

### 4.1. Điểm mạnh
* **Bảo mật & Phân quyền:** Hệ thống điều hướng và phân quyền giao diện cực kỳ rõ ràng giữa vai trò Thành viên và Thủ thư. Các thao tác trái phép đều bị chặn tốt.
* **Core Logic giao dịch:** Module mượn sách (REQ-04) hoạt động gần như hoàn hảo. Hệ thống kiểm soát chặt chẽ trạng thái sách ("Có sẵn", "Thất lạc", "Đang mượn") và giới hạn mượn (tối đa 3 sách) cũng như trạng thái tài khoản.
* **Giao diện người dùng (UI):** Thiết kế trực quan, dễ sử dụng, phản hồi thao tác nhanh.

### 4.2. Điểm yếu
* **Validate dữ liệu đầu vào (Input Validation):** Đây là điểm yếu lớn nhất. Module Quản lý User (Thủ thư) cấu hình Regex kiểm tra email sai trầm trọng, dẫn đến việc vừa chặn email đúng (BUG-04), lại vừa cho phép lưu email sai định dạng (BUG-05).
* **Trải nghiệm tìm kiếm (UX):** Ô tìm kiếm khá "cứng nhắc", không hỗ trợ loại bỏ khoảng trắng thừa (`trim()`), dễ khiến người dùng hiểu lầm hệ thống thiếu dữ liệu (BUG-01). Xung đột giữa Tìm kiếm và Lọc (BUG-02) cũng làm giảm hiệu quả tra cứu.
* **Quản lý quy trình kinh doanh (Business Logic):** Lỗ hổng trong việc không hiển thị thông báo thu phí phạt khi trả sách quá hạn (BUG-03) có thể gây thiệt hại trực tiếp cho hoạt động của thư viện.

---

## 5. Đề xuất ưu tiên sửa lỗi

> Nhóm đề xuất thứ tự ưu tiên dựa trên mức độ ảnh hưởng đến **Quy trình nghiệp vụ lõi (Business Logic)** và **Trải nghiệm người dùng (UX)**.

| Thứ tự | Bug | Mức độ | Lý do ưu tiên |
|--------|-----|--------|---------------|
| 1 | BUG-04 | High | Tính năng cốt lõi của Thủ thư. Lỗi này (chặn email đúng) trực tiếp **làm tê liệt chức năng thêm mới người dùng** vào hệ thống. Cần hotfix ngay lập tức bằng cách sửa Regex. |
| 2 | BUG-03 | High | Ảnh hưởng đến tài chính và quy trình phạt của thư viện. Thủ thư mất công cụ để nhận diện người dùng trả sách muộn ngay tại thời điểm trả. |
| 3 | BUG-05 | High | Nguy cơ tạo rác dữ liệu. Nếu hệ thống cho phép tạo tài khoản với email sai, các API gửi thư tự động (nhắc nhở quá hạn) sau này sẽ bị crash hệ thống. |
| 4 | BUG-02 | Medium | Sai logic truy vấn. Gây ức chế và sai lệch thông tin cho người dùng khi họ muốn tìm kiếm sâu (vừa search keyword vừa chọn thể loại). |
| 5 | BUG-01 | Medium | Trải nghiệm UX kém. Việc quên `trim()` khoảng trắng là lỗi sơ đẳng của lập trình viên Frontend, cần fix sớm để người dùng không tưởng nhầm thư viện thiếu sách. |

---

## 6. Kết luận

Dựa trên kết quả thực thi 30 Test Cases, hệ thống đạt tỷ lệ Pass là **83.33%**. Các tính năng cốt lõi phục vụ Thành viên (Xem sách, Mượn sách) hoạt động tương đối trơn tru.

**Tuy nhiên, hệ thống chưa sẵn sàng để phát hành.**

**Lý do:** Khối chức năng dành cho Thủ thư (Quản lý User) và xử lý quy trình trả sách đang tồn đọng 3 lỗi nghiêm trọng (High Severity: BUG-03, BUG-04, BUG-05). Các lỗi này phá vỡ luồng quản trị hệ thống và có nguy cơ sinh ra rác dữ liệu. Đội ngũ phát triển cần ưu tiên giải quyết dứt điểm các lỗi High này và bàn giao để nhóm QA kiểm thử hồi quy (Regression Test) trước khi có thể golive.

---

## 7. Bài học rút ra


---

## 8. Khai báo sử dụng AI

| Công cụ AI | Dùng cho phần nào | Bạn đã kiểm tra/chỉnh sửa thế nào |
|------------|-------------------|-----------------------------------|
| Gemini | Hỗ trợ phân tích kỹ thuật IDM, sinh format bảng biểu Markdown, rà soát cấu trúc Bug Report. | Nhóm lên ý tưởng test case, tự thực thi kiểm thử thủ công trên hệ thống thật để lấy kết quả (Fail/Pass). AI chỉ đóng vai trò thư ký tổng hợp, format dữ liệu và tư vấn viết bài. |
