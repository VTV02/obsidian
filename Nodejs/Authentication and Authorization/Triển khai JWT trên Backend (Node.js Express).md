Chúng ta sử dụng thư viện `jsonwebtoken` để tạo và xác minh `JWT`
### Cài đặt thư viện
```json
npm install jsonwebtoken bcryptjs
# bcryptjs để hash mật khẩu người dùng
```
### Công nghệ sử ddụng

- Nodejs - Runtime Javascript phía server
- Express.js - Web Framwork cho Nodejs
- MongoDB Atlas - CSDL NoSQL trên Cloud
- Mongoose 9 - ODM cho MongoDB
- JWT - Tạo và xác thực token
- bcryptjs - Mã hóa (hash) mật khẩu
- dotenv - quản lý biến môi trường
- cors - cho phép fronend gọi API cross-origin
- nodemon - từ độgn restart server khi code thay đôi
```js =
authentication-authorization/

├── app.js                    # File chính, khởi tạo server

├── config.js                 # Cấu hình JWT secret

├── config.env                # Biến môi trường
├── package.json              # Dependencies & scripts

├── controllers/

│   └── authController.js     # Logic xử lý đăng ký/đăng nhập

├── models/

│   └── User.js               # Schema & model người dùng

└── routes/

    └── authRoutes.js          # Định nghĩa routes API
```

Flow hoạt đông
Khi client gửi request đến server: 
●       1. Request đi qua middleware cors() → cho phép cross-origin

●       2. Request đi qua middleware express.json() → parse body JSON

●       3. Request được chuyển đến router phù hợp (authRoutes)

●       4. Router chuyển đến controller tương ứng (authController)

●       5. Controller xử lý logic, tương tác với Model (User)

●       6. Model tương tác với MongoDB thông qua Mongoose

●       7. Controller trả về response (JSON) cho client

Tại sao cần express.json? 
Khi client gửi request kiểu:
```http
POST /login
Content-Type: application/json
```
Body:
```json
{
  "email": "trung@gmail.com",
  "password": "123456"
}
```
Về bản chất thì HTTP gửi chuỗi `text thô` (raw string) khi server nhận được chỉ là stream dữ liệu text
Nếu không có `express.json` thì `req.body` sẽ là `undifined` 
Vậy `express.json` làm gì?
Nó là một `middleware parse` 
```js
app.use(express.json());
```
Kiểm tra header `Content-Type: application/json` 
Đọc `raw body`
`Parse JSON string -> Object javascript`
Gán vào `req.body`
Sau đó ta mới dùng được `req.body.email`
### File app.js - Entry Point

Đây alf file chín của ứng dụng, nơi khởi tạo Express server, connect db, đăng ký middleware + routes
```js
const express = require("express");
const cors = require("cors");
const app = express();
const dotenv = require("dotenv");
const mongoose = require("mongoose");
const authRoutes = require("./routes/authRoutes");
dotenv.config({ path: "./config.env" });
```
express: Web framework, tạo instance app để cấu hình server
cors: Middleware cho phép frontend ở port 5172 gọi backend port 5000 mà không bị chặn
dotenv: đọc file config.env và nạp vào biến process.env
mongoose: Thư viện ODM giúp tương tác với MongoDB bằng Javascript Objects
### Kết nối db

```js
const DB = process.env.DATABASE;

mongoose
  .connect(DB)
  .then(() => console.log("Connected to MongoDB"))
  .catch((err) => console.log(err));
```

Sử dụng connection string từ biến môi trường DATABASE (MongoDB Atlas). Hàm connect() trả về Promise:
●       Thành công → in "Connected to MongoDB"
●       Thất bại → in lỗi ra console
### Middleware & Routes

```js
app.use(cors());

app.use(express.json());

app.use("/api/auth", authRoutes);
```
**cors():** Cho phép mọi origin gọi API (phù hợp khi development).

**express.json():** Parse request body từ JSON thành JavaScript object, cho phép truy cập req.body.

**app.use("/api/auth", authRoutes):** Mọi request bắt đầu bằng /api/auth sẽ được xử lý bởi authRoutes router.

