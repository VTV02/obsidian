Một trong những pp phổ biến và mạnh mẽ nhất để triển khai xác thực là sử dụng `JSON Web Tokens`
JWT là một tiêu chuẩn mở (RFC-7519) định nghĩa một cách nhỏ gọn và tự chứa để truyền thông tin an toàn giữa các bên dưới dạng đối tượng JSON
### Cấu trúc JSON Web Tokens(JWT)
Một JWT không chỉ là một chuỗi ký tự ngẫu nhiên, nó có cấu trúc rõ ràng và được thiết kế để chứa thông tin xác thực. ***Mỗi JWT được chia thành ba phần, cách nhau bởi dấu chấm (`.`)***

1. ***Header(Tiêu đề)***: Chứa thông tin về loại token(thường là JWT) và thuật toán mã hóa được sử dụng để đăng ký token(ví dụ `HMAC SHA256 hoặc RSA`)
```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

Phần này sau đó được mã hóa Base64Url
2. ***Payload(tải trọng):*** chứa các `claims` những tuyến bố về một thực thể(thường là người dùng) và các dữ liệu bổ sung. Có 3 loại claims chính:
	1. Registered clainms: Các claims được định nghĩa trước và khuyến nghị sử dụng, nhưng không bắt buộc. í dụ: `iss` (issuer - nhà phát hành), `exp` (expiration time - thời gian hết hạn), `sub` (subject - chủ thể), `aud` (audience - đối tượng), v.v.
	2. - **Public claims:** Các claims có thể định nghĩa bởi bất kỳ ai nhưng cần tránh xung đột bằng cách đăng ký chúng trong IANA JSON Web Token Registry hoặc sử dụng URI có tên không gian.
	3. - **Private claims:** Các claims tùy chỉnh được tạo ra để chia sẻ thông tin giữa các bên tham gia, không có đăng ký chính thức và có thể xung đột nếu không cẩn thận.
	```json
	{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true,
  "iat": 1516239022,
  "exp": 1516242622 // Hết hạn sau 1 giờ
}
	```
Phần này cũng được mã hóa Base64Url.
3. **Signature (Chữ ký):** Được sử dụng để xác minh rằng token không bị thay đổi và được tạo bởi người gửi đã biết. Chữ ký được tạo bằng cách lấy header đã mã hóa, payload đã mã hóa, một khóa bí mật (secret key) và áp dụng thuật toán mã hóa đã chỉ định trong header.
```json
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret
)
```
Khi ứng dụng backend nhận được JWT, nó sẽ sử dụng cùng thuật toán và khóa bí mật để tạo lại chữ ký. Nếu chữ ký tạo lại khớp với chữ ký trong token, token được coi là hợp lệ và chưa bị giả mạo.
Tổng thể, một JWT hoàn chỉnh sẽ trông như thế này (sau khi mã hóa Base64Url):
```json
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyLCJhZ
```

> [JWT] JWT
> JWT là "tự chứa" (self-contained), nghĩa là tất cả thông tin cần thiết về người dùng (như ID, vai trò) đều nằm trong token. Điều này giúp giảm thiểu số lần truy vấn cơ sở dữ liệu để lấy thông tin người dùng, tăng hiệu suất cho các API stateless.
> 

### Cơ chế hoạt động của xác thực JWT
Hãy hình dung luồng xác thực người dùng với JWT giữa client (ứng dụng React) và server (Node.js/Express backend):
Client gửi thông tin đăng nhập(username + password,...) --> Server 
Server thực hiện X***ác thực thông tin đăng nhập với `DB`*** . ***Nếu họp lệ thì tạo JWT(Header + Payload + Signature)*** -->Trả JWT cho client. Client sẽ lưu JWT trong (localstorage, sessionStorage, cookies)
Trong mỗi lần yêu cầu tiếp theo thì sẽ gửi JWT(Header Authorization: Bearer <token>)
Server lại xác thực JWT: Kiểm tra Signature, Kiểm tra thời gian hết hạn (Expiration - 'exp' claim)
Lây thông tin người dùng từ `Payload`  nếu JWT hợp lệ thì xử lý yêu cầu về dữ liệu. Ngược lại thì báo lỗi
![[Pasted image 20260302161704.png]]
1. **Đăng nhập (Client gửi thông tin):** Người dùng nhập `username` và `password` trên giao diện người dùng của ứng dụng React. Client gửi yêu cầu POST đến endpoint đăng nhập trên server (ví dụ: `/api/login`).
2. **Xác thực trên Server:** Server nhận yêu cầu, kiểm tra `username` và `password` trong cơ sở dữ liệu.
3. **Tạo JWT:** Nếu thông tin đăng nhập hợp lệ, server sẽ tạo một JWT. Payload của JWT thường chứa `user ID`, `vai trò` (role) và thời gian hết hạn (`exp`). Server ký JWT bằng một khóa bí mật mà chỉ server biết.
4. **Trả về JWT:** Server gửi JWT này về cho client trong phản hồi HTTP (thường là trong body hoặc header).
5. **Lưu trữ JWT trên Client:** Client nhận JWT và lưu trữ nó. Các vị trí phổ biến để lưu trữ là `localStorage`, `sessionStorage`, hoặc `cookies`. Chúng ta sẽ thảo luận chi tiết hơn về ưu nhược điểm của từng cách lưu trữ sau.
6. **Gửi JWT trong các yêu cầu tiếp theo:** Với mỗi yêu cầu HTTP cần xác thực (ví dụ: lấy danh sách bài viết chỉ dành cho người dùng đã đăng nhập, tạo bài viết mới), client sẽ gửi JWT đã lưu trữ trong header `Authorization` dưới dạng `Bearer <token>`.
7. **Xác thực JWT trên Server:** Server nhận yêu cầu và trích xuất JWT từ header `Authorization`. Nó sẽ:
    - Xác minh chữ ký của JWT bằng khóa bí mật. Nếu chữ ký không khớp, token đã bị giả mạo.
    - Kiểm tra thời gian hết hạn (`exp` claim) của token. Nếu token đã hết hạn, nó không còn hợp lệ.
    - Nếu token hợp lệ, server sẽ giải mã payload và lấy thông tin người dùng (user ID, vai trò) để xác định quyền truy cập.
8. **Xử lý yêu cầu:** Nếu JWT hợp lệ và người dùng có quyền, server sẽ xử lý yêu cầu và trả về dữ liệu.
9. **Từ chối truy cập:** Nếu JWT không hợp lệ (sai chữ ký, hết hạn, không có token), server sẽ trả về lỗi `401 Unauthorized`.
