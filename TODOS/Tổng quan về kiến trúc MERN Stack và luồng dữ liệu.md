`MERN stack` là viết tắt của bốn công nghệ: MongoDB, Express, React, NodeJS. Đây là cả một hệ sinh thái Javascript toàn diện, cho phpes ta sử dụng cùng một ngôn ngữ lập trình cho cả frontend và backend

### Kiến trúc các thành phần trong MERN

Mỗi thành phần đóng vai trò như một mắt xích trong chuỗi xử lý dữ liệu
- `MongoDB`: Hệ quản trị cơ sở dữ liệu NoSQL, lưu trữ dữ liệu dưới dạng các tài liệu(documents) có cấu trúc tương tự JSON (gọi là BSON). Nó không yêu cầu các bảng cứng nhắc như SQL, cho  phép linh hoạt trong việc thay đỏi cấu trúc dữ liệu các tác vụ(task)
- Express.js: Framework chạy trên Nodejs dùng để xây dựng các API. Nó đóng vai rò trung gian: tiếp nhận yêu cầu từ client và tương tác với database gà gửi phản hồi
- React: Thư viện frontend giúp xây dựng giao diện người dùng dựa trên các component. React quản lý trạng thái va hiển thị dữ liệu nhận được từ Express
- Nodejs: Môi trường thực thi JavaScript phía server. Nó cho phép Express chạy và xử lý các yêu cầu mạng không đồng bộ (asynchronous)
### Luồng dữ liệu trong ứng dụng To-Do List

Trong ứng dụng này, luồng dữ liệu theo mô hình Request-Response. Khi người dùng thêm một "Task" mới, luồng vận hành sẽ diễn ra như sau:
- Frontend(React): Người dùng nhập nội dung vào form. Khi nhấn "Submit", React gửi một HTTP Request(thường là phương thức "POST") chứa dữ liệu của task đến địa chỉ API của server
- Backend(Express/Nodejs): Route tương ứng trong Express nhận request, kiểm tra tính hợp lệ của dữ liệu, sau đó sẽ yêu cầu Mongoose(Thư viện điều khiển MongoDB) lưu dữ liệu vào bộ sưu tập (collection) trong database.
- Database(MongoDB): Lư trữ tài liệu task và gửi xác nhận thành công về cho Express
- Phản hồi: Express gửi một HTTP Response (thường là dữ liệu vừa lưu dưới dạng JSON) về cho React. React nhận dữ liệu đó và cập nhật lại giao diện người dùng ngay lập tức mà không cần tải lại trang.
![[Pasted image 20260309091245.png]]
### Sự phân tách giữa Client và SERVER
Điểm côt lõi cần nắm vừng là sự phân tách giữa Client-side và Server-side. Client(React) chayj trình duyệt của người dùng, trong khi Server(Nodejs/ExpressJS) chạy phía máy chủ(hoặc môi trường Cloud). Chúng không chia sẻ bộ nhớ. Mọi thông tin cần trao đổi giữa hai bên phải thông qua giao thức HTTP(thường qua các API endpoint)

### Các khái niệm nền tảng trong giao tiếp dữ liệu

Mỗi giao tiếp giữa Client và Server dược thực hiện qua các phương thức HTTP:
- `GET`: Lấy dữ liệu từ Server (ví dụ: Lấy toàn bộ danh sách Task)
- `POST`: Gửi dữ liệu mưới lên Server ví dụ như thêm task mới
- `PUT/PATCH`: cập nhật dữ liệu hiện có ví dụ là đánh dấu task đã hoàn thành
- `DELETE` : Xóa dữ liệu, ví dụ là xóa 1 task
Kiến trúc MERN cho phép bạn đồng bộ hóa dữ liệu từ database đến giao diện người dùng thông qua các API endpoint. Hiểu rõ luồng request/response là điều kiện tiên quyết để tránh việc dữ liệu bị mất hoặc không đồng bộ giữa các lần cập nhật. Trong các phần tiếp theo, bạn sẽ thiết lập môi trường để bắt đầu hiện thực hóa luồng dữ liệu này từ database cho đến giao diện thực tế.
