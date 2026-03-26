Nodejs là môi trường thực thi Javascript phía server, cho phép chạy mã JS ngoài môi trường browser
Cốt lỗi `NodeJs` sử dụng engine V8 của Google Chrome để biên dịch Javascript sang mã máy, biến nó thành một nền tảng cực kỳ mạnh mẽ để xây dựng các ứng dụng mạng có khả năng mở rộng

#### Thiết lập môi trường phát triển `NodeJS`

Không nền cài đặt Nodejs trực tiếp từ trang chủ theo cách thông thường. Nên sử dụng `NVM` (Node Version Manager). Lý do là vì dự án khác nhau thường yêu cầu các phiên bản Node khác nhau. NVM cho phép chuyển đổi giữa các phiên bản này chỉ với một dòng lệnh

### Cấu trúc thư mục dự án Fullstack
Một dự án MERN (MongoDB, Express, React, Node) tiêu chuẩn cần sự tách biệt rõ ràng giữa logic backend và frontend để tránh xung đột mã nguồn và dễ dàng triển khai (deploy).

Cấu trúc gợi ý cho ứng dụng To-Do List:

```js
my-todo-app/
├── backend/            # Chứa API server và kết nối DB
│   ├── node_modules/
│   ├── controllers/    # Xử lý logic nghiệp vụ
│   ├── models/         # Định nghĩa Schema dữ liệu (MongoDB)
│   ├── routes/         # Định nghĩa các endpoint API
│   ├── .env            # Biến môi trường (cổng, kết nối DB)
│   ├── server.js       # File entry point của backend
│   └── package.json
├── frontend/           # Chứa giao diện React
│   ├── src/
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── package.json
└── README.md
```
### Tại sao lại chia thư mục như vậy?
- `Tách biệt(Separation of Concerns)`: `Backend và Fronted` có các `dependency` riêng biệt. Việc cài đặt `axios` ở `frontend` không liên quan đến cài `mongoose` ở `backend`. Mỗi thư mục có `package.json` riêng giúp quy trình cài đặt độc lập
- `Quản lý biến môi trường`: các thông tin nhạy cảm như `MOGO_URI` hoặc `JWT_SECRET` chỉ nên nằm trong thư mục `backend/.env`. Tuyệt đối không bao giờ được `push file` này lên Git. Hãy dùng `.gitignore`
- `Khả năng mở rộng`: Khi ứng dụng phức tạp hơn, bạn dễ dàng thêm các thư mục như `middleware` hoặc `utils` vào backend mà không làm rối cấu túc tổng thể
![[Pasted image 20260309163722.png]]
![[Pasted image 20260309165059.png]]
MgDB: 
VVT02/MgDb@vTv02
### Khởi tạo Backend với Express và kết nối Database MongoDB/Mongoose 

Express đóng vai trò như "Bô nõa" điều khiển các yêu cầu HTTP, trong khi Mongoose là cầu nối cho phép ứng dụng Nodejs giao tiếp với MongoDB băng cách sử dụng các đối tượng Javascript thay vì truy vấn thô. Viêc kết nối thành công hai thành phàn này là bước nền tảng 

#### Khởi tạo Express Server
```js
const express = require("express");
const mongoose = require("mongoose");

require('dotenv').config();

const app = express();

app.use(express.json());

```
