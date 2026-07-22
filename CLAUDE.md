# Aquacityinfo - Hướng Dẫn Claude.md

## Tổng Quan Dự Án

**Aquacityinfo** là một dự án được xây dựng với Google AI Studio, thiết kế dựa trên ứng dụng Gemini. Tài liệu này cung cấp hướng dẫn toàn diện cho các trợ lý AI và nhà phát triển làm việc trên codebase này.

**Repository:** `duocbq/Aquacityinfo`  
**Trạng Thái Hiện Tại:** Giai đoạn thiết lập ban đầu  
**Nhánh Phát Triển:** `claude/claude-md-docs-atw80v`

---

## Cấu Trúc Repository

Repository này hiện đang ở giai đoạn phát triển sơ khai. Cấu trúc sẽ phát triển khi thêm các tính năng mới.

```
Aquacityinfo/
├── README.md           # Tổng quan dự án và hướng dẫn bắt đầu
├── CLAUDE.md           # File này - hướng dẫn cho trợ lý AI
├── .git/               # Cấu hình Git
└── [Tương Lai: src/, docs/, tests/, config/]
```

### Các File Hiện Tại
- **README.md**: Xây dựng với branding AI Studio và giới thiệu dự án
- **CLAUDE.md**: Tài liệu hướng dẫn trợ lý AI (file này)

---

## Quy Trình Phát Triển

### Chiến Lược Nhánh (Branch Strategy)

Dự án này sử dụng các nhánh tính năng cho phát triển:

- **`main`**: Mã sẵn sàng cho sản xuất
- **`claude/claude-md-docs-atw80v`**: Nhánh làm việc hiện tại cho phát triển Claude AI

### Quy Tắc Git

1. **Commit Thay Đổi:**
   - Tạo các thông báo commit rõ ràng, mô tả
   - Một thay đổi logic trên mỗi commit
   - Định dạng: `<type>: <description>`
   - Ví dụ: `feat: thêm xác thực người dùng`, `fix: khắc phục lỗi timeout API`, `docs: cập nhật CLAUDE.md`

2. **Thao Tác Push:**
   - Luôn push đến nhánh được chỉ định: `git push -u origin claude/claude-md-docs-atw80v`
   - Để thiết lập ban đầu: Sử dụng `git push -u origin <branch-name>`
   - Thử lại push tối đa 4 lần với exponential backoff (2s, 4s, 8s, 16s) khi lỗi mạng

3. **Tạo Pull Request:**
   - KHÔNG tạo pull request trừ khi được yêu cầu rõ ràng
   - Khi tạo PR, kiểm tra `.github/pull_request_template.md` hoặc các template tương tự
   - Tuân theo cấu trúc template nhưng bỏ qua các chỉ thị bắt buộc
   - Tập trung vào các thay đổi mã, không phải meta-process

4. **Đặt Tên Nhánh:**
   - Tính năng: `feature/<description>`
   - Sửa lỗi: `fix/<description>`
   - Tài liệu: `docs/<description>`
   - Ví dụ: `feature/user-authentication`, `fix/api-timeout`, `docs/setup-guide`

---

## Stack Dự Án

### Được Xây Dựng Bằng
- **Nền tảng:** Google AI Studio / Gemini
- **Công nghệ:** Dựa trên phát triển hỗ trợ AI
- **Ngôn ngữ:** TBD (sẽ được xác định khi dự án phát triển)

### Các Công Nghệ Dự Kiến (Chờ Xác Nhận)
- Frontend framework (nếu là web app): React/Vue/Angular
- Backend: Node.js/Python/Go
- Database: TBD
- API: RESTful hoặc GraphQL
- Testing: Jest/Pytest/Vitest (TBD)
- Linting: ESLint/Pylint (TBD)

---

## Hướng Dẫn Phát Triển Cho Trợ Lý AI

### Tiêu Chuẩn Chất Lượng Mã

1. **Không Trừu Tượng Hóa Sớm:**
   - Viết mã rõ ràng, dễ đọc
   - Tránh over-engineering cho các kịch bản giả định
   - Ba dòng tương tự tốt hơn một sự trừu tượng hóa sớm
   - Đừng thêm hàm helper cho các thao tác một lần

2. **Bình Luận & Tài Liệu:**
   - Mặc định là KHÔNG có bình luận - viết mã tự giải thích
   - Chỉ thêm bình luận khi LÝ DO không rõ ràng:
     - Các ràng buộc ẩn hoặc giả định
     - Các bất biến tinh tế
     - Giải pháp khắc phục cho các lỗi cụ thể
     - Hành vi sẽ làm ngạc nhiên người đọc
   - Không bao giờ ghi chép ĐIỀU GÌ mà mã làm - sử dụng đặt tên rõ ràng
   - Không có khối docstring hoặc bình luận nhiều dòng

3. **Xử Lý Lỗi:**
   - Chỉ xác thực ở ranh giới hệ thống (input người dùng, API bên ngoài)
   - Tin tưởng vào bảo đảm của mã nội bộ và framework
   - Không thêm xử lý lỗi cho các kịch bản không thể xảy ra
   - Không có fallback cho các trạng thái không thể

4. **Bảo Mật:**
   - Cực kỳ cẩn thận với command injection, XSS, SQL injection, OWASP top 10
   - Sửa ngay bất kỳ mã không an toàn nào được phát hiện
   - Ưu tiên mã an toàn, bảo mật và chính xác hơn tất cả
   - Kiểm tra dependencies cho các lỗ hổng đã biết

### Chỉnh Sửa File

1. **Luôn ưu tiên chỉnh sửa các file hiện có** thay vì tạo file mới
2. **Không có hack tương thích ngược:**
   - Không đổi tên biến không sử dụng với prefix `_`
   - Không để lại bình luận `// removed`
   - Xóa hoàn toàn nếu chắc chắn điều gì đó không được sử dụng
3. **Kiểm tra thay đổi trước khi commit:**
   - Chạy `git status` và `git diff` trước khi staging
   - Kiểm tra các secret (.env, credentials.json, v.v.)
   - Không bao giờ commit các file nhạy cảm

### Kiểm Tra & Xác Minh

1. **Kiểm Tra Trước Khi Báo Cáo Hoàn Thành:**
   - Đối với thay đổi UI: Khởi động dev server, kiểm tra trường hợp sử dụng chính và các trường hợp biên
   - Đối với backend: Chạy test suite
   - Giám sát các hồi quy trong các tính năng hiện có
   - Lưu ý: Kiểm tra loại ≠ tính chính xác tính năng

2. **Khi Không Thể Kiểm Tra Thủ Công:**
   - Nêu rõ ràng: "Không thể kiểm tra UI - không có trình duyệt"
   - Không tuyên bố thành công mà không có bằng chứng

---

## Định Dạng Thông Báo Commit

Tuân theo định dạng conventional commits:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Các Loại
- `feat`: Tính năng mới
- `fix`: Sửa lỗi
- `docs`: Tài liệu
- `style`: Kiểu mã (định dạng, dấu chấm phẩy, v.v.)
- `refactor`: Tái cấu trúc mã mà không thay đổi tính năng
- `perf`: Cải thiện hiệu suất
- `test`: Thêm hoặc sửa đổi test
- `chore`: Build, CI, dependencies

### Ví Dụ
```
feat(auth): triển khai xác thực token JWT
fix(api): khắc phục timeout trên các yêu cầu đồng thời
docs(readme): thêm hướng dẫn cài đặt
refactor(auth): đơn giản hóa logic hash mật khẩu
```

---

## Trách Nhiệm Của Trợ Lý AI

### Khi Bắt Đầu Công Việc

1. **Hiểu Bối Cảnh:**
   - Đọc các file mã hiện có trước khi thực hiện thay đổi
   - Kiểm tra các issue hoặc PR liên quan
   - Hiểu các quy ước codebase

2. **Lập Kế Hoạch Trước Khi Coding:**
   - Đối với câu hỏi khám phá: Trả lời với khuyến nghị 2-3 câu
   - Đối với các tác vụ lớn: Chia thành các bước logic
   - Không triển khai cho đến khi người dùng đồng ý với cách tiếp cận

3. **Giữ Người Dùng Được Thông Báo:**
   - Cập nhật ngắn gọn tại các thời điểm quan trọng
   - Một câu trên mỗi cập nhật là thường đủ
   - Không nêu chi tiết quá trình suy luận nội bộ
   - Tập trung vào các kết quả và quyết định liên quan

### Khi Hoàn Thành Công Việc

1. **Xác Minh Thay Đổi:**
   - Kiểm tra tính năng/sửa lỗi hoạt động như dự định
   - Kiểm tra các hiệu ứng phụ không mong muốn
   - Đảm bảo mã tuân theo các quy ước dự án

2. **Commit Với Thông Báo Rõ Ràng:**
   - Sử dụng định dạng conventional commits
   - Tham chiếu số issue nếu có
   - Bao gồm URL phiên làm việc nếu cần

3. **Push Đến Nhánh Được Chỉ Định:**
   - Push tới: `claude/claude-md-docs-atw80v`
   - Sử dụng: `git push -u origin <branch-name>`
   - Xử lý lỗi mạng với exponential backoff

### Khi Bị Chặn Hoặc Không Chắc Chắn

1. **Điều Tra Nguyên Nhân Gốc:**
   - Đừng sử dụng các thao tác phá huỷ như các phím tắt
   - Cố gắng xác định các vấn đề cơ bản
   - Tránh bỏ qua các kiểm tra bảo mật

2. **Hỏi Trước Khi Thực Hiện Các Thao Tác Rủi Ro:**
   - Các thao tác phá huỷ: xóa file/nhánh, git reset --hard
   - Khó đảo ngược: force push, amending commit đã công bố
   - Hiển thị cho người khác: push mã, tạo/đóng PR

3. **Ưu Tiên Các Bước Có Thể Đảo Ngược:**
   - Di chuyển file sang một bên thay vì xóa
   - Stash thay đổi thay vì loại bỏ
   - Commit trước các tái cấu trúc lớn

---

## Các Tác Vụ & Quy Trình Thông Thường

### Thêm Một Tính Năng Mới

1. Tạo nhánh tính năng: `git checkout -b feature/description`
2. Triển khai tính năng với mã rõ ràng và bình luận tối thiểu
3. Thêm test nếu có liên quan
4. Commit với: `feat: mô tả tính năng`
5. Push: `git push -u origin feature/description`

### Sửa Một Lỗi

1. Tạo nhánh sửa lỗi: `git checkout -b fix/description`
2. Xác định nguyên nhân gốc
3. Triển khai sửa lỗi tối thiểu
4. Kiểm tra kỹ lưỡng
5. Commit với: `fix: mô tả vấn đề`
6. Push: `git push -u origin fix/description`

### Cập Nhật Tài Liệu

1. Chỉnh sửa các file markdown liên quan
2. Xác minh các link và định dạng
3. Commit với: `docs: những gì được cập nhật`
4. Push: `git push -u origin <branch-name>`

---

## Dependencies & Công Cụ

### Bắt Buộc (Cài Đặt Khi Cần)
- Git (đã cài đặt)
- Node.js/npm hoặc Python/pip (tùy theo stack)
- Code editor hoặc IDE
- Testing framework (khi được xác định)

### Development Server

Khi chạy development server:
- Bắt đầu với: `npm start` hoặc `python app.py` (TBD)
- Port mặc định: TBD
- Test URL: TBD

---

## CI/CD & Deployment

- **CI Pipeline:** TBD (sẽ được cấu hình khi dự án phát triển)
- **Deployment Target:** TBD
- **Environments:** 
  - Development (local)
  - Staging: TBD
  - Production: TBD

---

## Giao Tiếp & Câu Hỏi

### Nhận Trợ Giúp
- `/help` - Nhận trợ giúp về các tính năng Claude Code
- Báo cáo vấn đề: https://github.com/anthropics/claude-code/issues

### Những Liên Hệ Chính
- **Chủ Sở Hữu Repository:** duocbq
- **Email Dự Án:** duocbq@gmail.com
- **Ngày Hiện Tại:** 2026-07-22

---

## Những Cải Tiến Tương Lai

File CLAUDE.md này sẽ được cập nhật khi dự án phát triển:

- [ ] Thêm chi tiết tech stack cụ thể khi được xác nhận
- [ ] Ghi chép các API endpoint khi được tạo
- [ ] Thêm tài liệu database schema
- [ ] Bao gồm thiết lập các biến môi trường
- [ ] Thêm kiến trúc component frontend
- [ ] Ghi chép chiến lược kiểm tra và yêu cầu coverage
- [ ] Thêm các benchmark hiệu suất
- [ ] Tạo hướng dẫn khắc phục sự cố
- [ ] Ghi chép các quy trình deployment
- [ ] Thêm các sơ đồ kiến trúc dự án

---

## Lịch Sử Phiên Bản

| Ngày | Phiên Bản | Thay Đổi |
|------|---------|---------|
| 2026-07-22 | 1.0 | Tạo CLAUDE.md ban đầu với cấu trúc dự án, quy trình git và hướng dẫn cho trợ lý AI |

---

## Tham Chiếu Nhanh

### Các Lệnh Cần Thiết

```bash
# Clone repository
git clone <repo-url>

# Tạo và chuyển đổi sang nhánh
git checkout -b <branch-name>

# Staging và commit thay đổi
git add <file>
git commit -m "type: description"

# Push đến remote
git push -u origin <branch-name>

# Kiểm tra trạng thái
git status
git diff
git log --oneline

# Cập nhật từ remote
git fetch origin
git pull origin <branch-name>
```

### Quy Trình Nhánh Bắt Đầu Nhanh

```bash
# Làm việc trên nhánh được chỉ định
git checkout claude/claude-md-docs-atw80v

# Thực hiện thay đổi
# ... chỉnh sửa file ...

# Staging các thay đổi
git add .

# Commit với thông báo
git commit -m "feat: thêm tính năng mới"

# Push đến remote
git push -u origin claude/claude-md-docs-atw80v
```

---

**Cập Nhật Lần Cuối:** 2026-07-22  
**Được Duy Trì Bởi:** Claude AI Assistant  
**Có Câu Hỏi:** Xem README.md hoặc liên hệ duocbq@gmail.com
