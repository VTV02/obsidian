Trong ứng dụng web đặc biệt là các ứng dụng Fullstack như ngày nay thì việc kiểm soát ai có thể truy cập tìa nguyên là vô cùng quan trọng. Đây chính là lúc ta cần đến cơ chế xác thực `Authentication` và phần quyền `Authorization`. Hai khái niệm này đi đôi với nhau, nhưng có vai trò hoàn toàn khác biệt. `Authentication` là quá trình xác thực xem, bạn là ai? Otherwise `Authorization` là những gì người dùng đó được phép làm sau khi đã qua `Authentication` hay nói cách khác `Authorization` xác nhận là bạn có quyền được làm gì?

### Authentication 
Đơn giản nó dùng để chứng minh rằng người dùng hoặc hệ thống nào đó là người mà họ tự nhận. Giống như bạn vô một toàn nhà thì việc bạn đưa thẻ CCCD cho lễ tân mục đích là để xác thực là bạn là 'Lan' chứ không phải là 'Nam'

Các hình thức xác thực bao gồm: 
- ***Tên người dùng và Mật khẩu(Username & Password)***: Đây là cách phổ biến nhất và tối thiểu nhất của một hệ thống. Hệ thống sẽ so sánh thông tin này với dữ liệu đã được lưu trữ(thường dữ liệu được lưu trữ sẽ được hash) để xác minh.
- ***Xác thực đa yếu tố(Multi-Factor Authentication - MFA)***:  Đây là cách giúp tăng cường bảo mật bằng cách yêu cầu cung cấp nhiều hơn một loại bằng chứng. Ví dụ ngoài Username và Password còn cần thêm OTP hoặc Finger-Factor
- ***Xác thực dựa trên Token(Token-based Authentication):***  Sau khi xác thực thành công lần đầu(thương là đối với Username & Password ) thì hệ thống sẽ cấp cho người dùng **1 Token**. Token này sau đó thường sẽ được sử dụng trong các yêu cầu tiếp theo để chứng minh danh tính mà không cần phải dùng tới username hay password. JWT (JSON Web Tokens) là một ví dụ
- ***Xác thực bằng OAuth/OpenID Connect:***  Các dịch vụ bên thứ ba như(Google, Facebook) xác thực người dùng thay cho ứng dụng của ta, giúp người dùng không cần tạo tài khoản mới
### Authorization 
Sau khi hệ thống đã xác thực được bạn là ai, bước tiếp theo sẽ là bạn được làm gì?
Nó liên quan đến `role` và `permission` gắn liền với danh tính của người đó. 
- ***Phân quyền dựa trên vai trò(Role-Based Access Control - RBAC)*** : Đây là mô hình phổ biến nhất. Người dùng sẽ được gán các vai trò như: `admin` , `editor`, `viewer`, `guest` . Mỗi vai trò sẽ có tập họp quyền nhất định
- `admin`: có thể tạo, đọc, cập nhật, xóa (CRUD) tất cả các bài viết, quản lý người dùng.
- `editor`: chỉ có thể CRUD các bài viết của chính họ, đọc bài viết của người khác.
- `viewer`: chỉ có thể đọc bài viết. Ưu điểm của RBAC là dễ quản lý, đặc biệt khi số lượng người dùng và quyền hạn tăng lên. Bạn chỉ cần thay đổi quyền của vai trò, mọi người dùng thuộc vai trò đó sẽ được cập nhật.
- **Phân quyền dựa trên quyền hạn (Permission-Based Access Control):** Mỗi người dùng hoặc tài nguyên được gán trực tiếp các quyền cụ thể (ví dụ: `can_edit_post_123`, `can_delete_user_456`). Mô hình này linh hoạt hơn RBAC nhưng có thể trở nên khó quản lý khi số lượng quyền và người dùng lớn.
- - **Phân quyền dựa trên thuộc tính (Attribute-Based Access Control - ABAC):** Đây là mô hình nâng cao, dựa trên các thuộc tính của người dùng (tuổi, vị trí, phòng ban), của tài nguyên (loại tài liệu, độ nhạy cảm), và của môi trường (thời gian trong ngày, vị trí mạng). Ví dụ: "Người quản lý chỉ có thể truy cập báo cáo tài chính trong giờ hành chính từ mạng nội bộ."
## Luồng hoạt động của Xác thực và Phân quyền

Để hình dung rõ hơn, hãy xem luồng cơ bản của quá trình xác thực và phân quyền trong một ứng dụng web sử dụng token.
![[Pasted image 20260302153633.png]]
## Lý do cần Xác thực và Phân quyền

Việc có cơ chế xác thực và phân quyền mạnh mẽ không chỉ là một tính năng bổ sung mà là một yêu cầu cơ bản đối với bất kỳ ứng dụng nào xử lý dữ liệu người dùng hoặc có các chức năng nhạy cảm.

- **Bảo mật dữ liệu:** Ngăn chặn truy cập trái phép vào thông tin nhạy cảm của người dùng (email, thông tin cá nhân) hoặc dữ liệu quan trọng của ứng dụng (báo cáo, cài đặt).
- **Toàn vẹn dữ liệu:** Đảm bảo rằng chỉ những người dùng được phép mới có thể tạo, chỉnh sửa hoặc xóa dữ liệu, tránh tình trạng phá hoại hoặc lỗi dữ liệu do người dùng không có quyền gây ra.
- **Trải nghiệm người dùng cá nhân hóa:** Cho phép hiển thị các giao diện và chức năng khác nhau tùy thuộc vào vai trò của người dùng. Ví dụ, một admin sẽ thấy bảng điều khiển quản lý người dùng, trong khi người dùng thông thường thì không.
- **Tuân thủ quy định:** Nhiều quy định pháp lý (như GDPR, HIPAA) yêu cầu các ứng dụng phải có các biện pháp bảo mật mạnh mẽ để bảo vệ dữ liệu người dùng.
- **Kiểm toán và theo dõi:** Khi có vấn đề xảy ra, hệ thống xác thực và phân quyền giúp bạn truy ngược lại ai đã làm gì, vào thời điểm nào.
