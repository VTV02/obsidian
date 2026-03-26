Phương thức:
`GET` :
- Lấy tất cả người dùng: `GET /users`
- Lấy thông tin người dùng cụ thể: `GET /users/123`
- Lấy danh sách sản phẩm theo danh mục: `GET /product?category=electronics`
`POST` : gửi thông tin trong body của request 
- Tạo người dùng mới: `POST /users`
- Thêm một bài viết mới: `POST /posts`
- Gửi một đơn hàng: `POST /orders`
`PUT`: cập nhật thông tin
- Cập nhật toàn bộ thông tin của người dùng có ID 123: `PUT /user/123`
`DELETE`: Dùng để xóa 1 tài nguyên được chỉ định
- Xóa người dùng có ID 123: `DELETE /user/123`
- Xóa bài viết: `DELETE /posts/456`
### TRIỂN KHAI Routing trong Express.js

Trong Express, bạn định nghĩa các route bằng cách sử dụng các phưogn thức của đối tượng `app` (là `instance` của Express) hoặc một đối tượng `Router` 
#### Cấu trúc cơ bản của một `Route` 
Một `route` trong Express có dạng: `app.METHOD(PATH, HANDLLER)`:
- `app`: là một instance của Express
- `METHOD`: là một phương thức HTTP ví dụ như `get post put delete`
- `HANDLER`: là một hàm hoặc một mảng các hàm sẽ được thực thi khi `route` khớp. Hàm này có dạng `(req,res)` `=> {...}` , trong đó `req` là đối tượng `request` và `res` là đối tượng `response` 
```js
const express = require("express");
const app = express();
const port = 3000;

//Route cho phương thức GET
app.get('/', (req, res) =>{
res.send("Chao mung den voi server");
});

//Route cho phuong thuc POST
app.post('/items',(req,res)=>{
//logic de tao mot item moi
//res.send("Tao item thanh cong");
res.status()201_.send('Item created successfully!');
})

//Route cho phuong thuc GET de lay danh muc
app.get('/items',(req,res)=>{
const items = ['item 1', 'item 2', 'item 3'];
res.json(items);
})

// Route cho phuong thuc GET de lay mot muc cu the theo ID
app.get('/itmes/:id',(req,res)=>{
const itemId = req.params.id;
if(itemId === '1') {
res.json({id: itemId, name: 'Sample', description: 'This is a sample item'});
}
else {
res.status(404).send({message: .....})
}
})

//Route cho phuong thuc PUT de cap nhat mot muccu the theo ID
app.put('/items/:id', (req,res)=>{
const itemId = req.params.id;
//gia su body request chua du lieu cap nhat
//const updateData = req.body; //se hoc cach xu ly req.body sau
res.send(`Update ${itemId} successfully!`)
})

//Route cho phuong thuc DELETE de xoa mot muc cu the theo ID
app.delete('/item/:id',(req,res)=>{
const itemId = req.params.id;
res.send(`Xoa item ${itemId} successfully!`);
});

//Khoi dong server
app.listen(port, ()=>{
........
})

```
- Express cho phép định nghĩa các `path parameters` bằng cách sử dụng dấu hai chấm `:`
Đối tượng `req` và `res`:
- `req`: Đối tượng này chứa tất cả thông tin về yêu cầu HTTP đến, bao gồm `headers`, `body`, `parameters`, `query string`,...
- `res`: Đối tượng này dùng để gửi phàn hồi HTTP về cho client, bao gồm `status code`, `headers`, `body`
Một số phương thức với `res` thường dùng:
- `res.send(body)`: gửi một phản hồi văn bản hoặc HTML
- `res.json(obj)`: gửi một phản hồi JSON. Tự động thiết lập header `Content-Type` là `application/json`
- `res.status(code)`: thiết lập mã trạng thái HTTP(ví dụ: `200`, `201`, `404`, `500`) sau đó thường bạn sẽ gọi thêm là `.send()` hoặc `.json`
- `res.end()`: kết thúc quá trình phản hồi mà ko có dữ liệu
#### Route Order(Thứ tự Route)
Express xử lý các routes theo thứ tự được định nghĩa. Nếu ó nhiều routes khớp với mọt yêu cầu, chỉ route được định nghĩa đầu tiên được thực thi

### Xử lý requestion body và query parameters

Khi làm việc với HTTP API , dữ liệu được gửi đến server chủ yếu thông qua 2 con đường trên
#### Truy vấn dữ liệu với Query Parameters
Query parameters là các cặp key-value xuất hiện sau dấm chấm hỏi(`?`) trong URL. Thường được dùng cho các thao tác tìm kiếm, lọc và phân trang - những trường hợp không làm thay đổi tài nguyên trên server
Ví dụ: URL `/products?category=electronics&sort=price`, server cần biết client đang muốn lọc theo danh mục nào và sắp xếp ra sao. Trong Express, các tham số này được lưu trữ trng đối tượng `req.query`
```js
const express = require('express');
const app = express();

app.get('/search', (req, res) => {
  // req.query là một object chứa tất cả các tham số sau dấu ?
  const { category, sort } = req.query;

  res.send(`Đang tìm kiếm sản phẩm thuộc danh mục: ${category}, thứ tự sắp xếp: ${sort}`);
});

app.listen(3000);
```
`Lưu ý: req.query` luôn trả về giá trị dạng `string`. Nếu nhận vào số, hãy luôn ép kiểu nó. `parseInt(req.query.page`)`
### Truyền dữ liệu qua Request Body

Request Body được sử dụng trong các phương thức `POST`, `PUT`, `PATCH`. Khi ta cần gửi một lượng dữ liệu lớn hoặc có cấu trúc phức tạp thường là JSON để tạo mới hoặc cập nhạt tài nguyên
`Để đọc được nội dung từ Body` thì Express cần một `middleware` để phân tích `parse` luồng dữ liệu gửi đến thành `object Javascript` . Nếu không có bước này, `req.body` sẽ là `undefined`
```js
//Middleware nay cuc ky quan trong, no giup express hieu dinh dang JSON
app.use(express.json());

app.post('/users',(req,res)=>{
//Bay gio req.body da san sang truy cap
const {username, email} = req.body

})
```

### Sử dụng Middleware để thêm chức năng cho ứng dụng

`Middleware` trong Express là các hàm có quyền truy cập vào đối tượng yêu cầu `req` , đối tượng phản hồi `res` và hàm  `next` trong chu kỳ yêu cầu - phản hồi của ứng dụng. Khi một request gửi đến server, nó sẽ đi qua một chuỗi các `middleware` trước khi tới `route handler cuối cùng`
### Cơ chế hoạt động của Middleware

Mỗi middleware có thể thực hiện mã logic, thay đổi đối tượng request/response, hoặc kết thúc chu kỳ yêu cầu - phản hồi bằng cách gửi phản hồi về cho client. Nếu mọi thứ ok ở middleware này thì nó phải gọi hàm `next()` để  chuyển quyền xử lý cho middleware tiếp theo trong ngăn xếp
![[Pasted image 20260307103557.png]]
```js
const express = require('express');
const app = express();

// Middleware ghi log
const logger = (req, res, next) => {
  console.log(`${req.method} ${req.url} - ${new Date().toISOString()}`);
  next(); // Bắt buộc gọi để chuyển sang bước tiếp theo
};

app.use(logger); // Áp dụng cho mọi route

app.get('/', (req, res) => {
  res.send('Trang chủ');
});

app.listen(3000);
```
### Phân loại Middleware

Trong một ứng dụng thực tế, middleware được phân loại dựa trên phạm vi hoạt động:

- **Application-level middleware:** Được gắn vào đối tượng `app` thông qua `app.use()` hoặc `app.METHOD()`. Nó chạy cho mọi request hoặc các route cụ thể.
- **Router-level middleware:** Tương tự application-level nhưng gắn vào đối tượng `express.Router()`. Hữu ích để chia tách logic theo module (ví dụ: nhóm route `/users`).
- **Built-in middleware:** Express cung cấp sẵn các middleware như `express.json()` (để parse body dạng JSON) hoặc `express.static()` (để phục vụ file tĩnh như ảnh, CSS).
- **Third-party middleware:** Các thư viện bên thứ ba giúp giải quyết các bài toán cụ thể như `morgan` (logging chuyên nghiệp), `cors` (xử lý quyền truy cập chéo tên miền), hoặc `helmet` (bảo mật HTTP header).

