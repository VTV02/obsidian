Routes xác định các endpoint của ứng dụng và cách phản ứng với các HTTP
Controllers là nới chứ logic xử lý các yêu cầu , tách biệt khỏi phần Routes
### Vai trò của Routes
- Mỗi route là sự kết hợp của một phương thức HTTP(GET, POST, PUT, DELETE, ...), một đường dẫn URL(path) và một hoặc nhiều hàm xử lý. Khi một request HTTP đến server, Express sẽ khớp yêu cầu đó với các routes đã được định nghĩa.
```
// server.js (hoặc app.js)
const express = require('express');
const app = express();
const port = 3000;

// Route đơn giản
app.get('/', (req, res) => {
  res.send('Chào mừng đến với API của tôi!');
});

app.get('/api/posts', (req, res) => {
  // Logic xử lý để lấy danh sách bài viết sẽ ở đây
  const posts = [
    { id: 1, title: 'Bài viết 1', content: 'Nội dung bài viết 1' },
    { id: 2, title: 'Bài viết 2', content: 'Nội dung bài viết 2' },
  ];
  res.json(posts); // Trả về JSON
});

app.post('/api/posts', (req, res) => {
  // Logic để tạo bài viết mới
  // req.body sẽ chứa dữ liệu gửi lên (nếu có middleware xử lý body)
  res.status(201).send('Bài viết đã được tạo thành công.'); // Trả về trạng thái 201 Created
});

app.listen(port, () => {
  console.log(`Server đang chạy tại http://localhost:${port}`);
});
```
1. Tại sao phải tạo nội dung (mảng `posts`) bên trong `app.get`?

Hàm `app.get('/api/posts', ...)` là cách bạn định nghĩa một "địa chỉ" trên server. Khi có ai đó (trình duyệt, ứng dụng điện thoại, hoặc một trang web frontend như React/Vue) truy cập vào địa chỉ này, server cần có dữ liệu để trả về cho họ.

- **Dữ liệu giả lập (Mock data):** Trong ví dụ này, bạn đang tự tạo một mảng `posts` cứng (hardcode) ngay trong route. Điều này rất phổ biến khi mới học hoặc khi bạn muốn test API nhanh chóng.
    
- **Thực tế với Database:** Trong các dự án thực tế, bạn sẽ **không** viết cứng nội dung này. Thay vào đó, đoạn code bên trong `app.get` sẽ là những câu lệnh kết nối và **lấy dữ liệu từ Cơ sở dữ liệu** (như MySQL, MongoDB, PostgreSQL). Mảng `posts` lúc đó sẽ là kết quả được trả về từ Database.
    

2. Dùng `.json()` để làm gì?

Khi bạn dùng `res.json(posts)`, bạn đang nói với Express rằng: _"Hãy trả dữ liệu này về cho người dùng dưới định dạng JSON"_.

JSON (JavaScript Object Notation) là một chuẩn định dạng dữ liệu cực kỳ phổ biến. Có 3 lý do chính khiến ta phải dùng nó ở đây:

- **Ngôn ngữ chung giữa Frontend và Backend:** Khi Frontend nhận dữ liệu về, họ cần nó ở dạng cấu trúc (mảng, đối tượng) để có thể dùng vòng lặp (như `.map()`) hiển thị từng bài viết lên màn hình. Nếu bạn chỉ gửi text thuần thì Frontend sẽ rất khó để bóc tách thông tin.
    
- **Tự động chuyển đổi:** Trong Javascript, `posts` là một mảng object. Hàm `res.json()` sẽ tự động chuyển đổi mảng này thành một chuỗi văn bản định dạng JSON chuẩn xác trước khi gửi đi qua mạng internet.
    
- **Tự động cài đặt Header (Thông báo chuẩn):** Hàm `res.json()` sẽ ngầm đính kèm một thông báo (header) là `Content-Type: application/json`. Điều này giúp Frontend hoặc trình duyệt ngay lập tức nhận diện được _"À, đây là dữ liệu cấu trúc JSON, không phải là trang web HTML hay văn bản thuần"_, từ đó xử lý nó đúng cách.
    

---

**Tóm lại:**

- `res.send("Welcome to my Server")`: Dùng để gửi văn bản thuần hoặc HTML trực tiếp cho người dùng đọc.
    
- `res.json(posts)`: Dùng để gửi dữ liệu có cấu trúc cho các phần mềm/ứng dụng khác (Frontend) đọc và xử lý.
.GET ta chỉ đang lấy dữ liệu từ dữ liệu giả lập hoặc dữ liệu từ database sau đó `response` lại cho Frontend
. POST ta nhận bưu kiện, thông tin ví dụ như tạo bài viết mới từ Frontend và ta sẽ lưu nó xuống DB
Trong ví dụ trên, các hàm `(req, res) => { ... }` chính là các handler function. Chúng nhận vào hai đối số quan trọng:

- `req` (request object): Chứa thông tin về yêu cầu HTTP đến, bao gồm headers, parameters, body, query strings, v.v.
- `res` (response object): Dùng để gửi phản hồi trở lại client, bao gồm trạng thái HTTP, headers và dữ liệu (ví dụ: JSON, HTML, văn bản).
### Vai trò của Controllers
Khi ứng dụng có nhiều routes, việc nhồi nhét tất cả logic xử lý vòa trưc tiếp trong route handler sẽ khiến mã nguồn trở nên lộn xộn và khó uqanr lý. Đây là lúc `Controllers` phát huy tác dụng.
Một controller là một module hoặc một đối tượng chứa các hàm(thường gọi là `action methods` ) để xử lý các yêu cầu đến. Mỗi hàm trong controller thường tương ứng với một hành động cụ thể trên một tài nguyên (ví dụ: `getPosts` , `createPost` , `getPostById` , `updatePost` , `deletePost` )
Lợi ích của việc sử dụng controller:
- Tách biệt mối quan tâm(Separation of Concerns): Logic xử lý nghiệp vụ được tách ra khỏi logic định tuyến, giúp mã nguồn rõ ràng hơn.
- Tái sử dụng mã: Dễ dàng tái sử dụng các controller actions ở nhiều routes khác nhau
- Dễ kiểm thử: Việc kiểm thử các hàm controller độc lập sẽ dễ dàng so với kiểm thử các route handler lớn
- Dễ bảo trì: Khi có thay đổi logic nghiệp vụ, bạn chỉ cần sửa đổi trong controller mà không ảnh hưởng tới routes

```js
// controllers/postController.js
exports.getPosts = (req, res) => {
  // Logic để lấy danh sách bài viết từ cơ sở dữ liệu (sẽ học sau)
  const posts = [
    { id: 1, title: 'Bài viết 1', content: 'Nội dung bài viết 1' },
    { id: 2, title: 'Bài viết 2', content: 'Nội dung bài viết 2' },
  ];
  res.json(posts);
};

exports.createPost = (req, res) => {
  // Logic để tạo bài viết mới
  const newPost = req.body; // Giả sử dữ liệu bài viết mới nằm trong req.body
  console.log('Tạo bài viết mới:', newPost);
  res.status(201).json({ message: 'Bài viết đã được tạo thành công.', post: newPost });
};

exports.getPostById = (req, res) => {
  const postId = req.params.id; // Lấy ID từ URL
  // Logic để lấy bài viết theo ID từ cơ sở dữ liệu
  const post = { id: postId, title: `Bài viết ${postId}`, content: `Nội dung bài viết ${postId}` };
  if (post.id === '3') { // Ví dụ đơn giản cho trường hợp không tìm thấy
    return res.status(404).json({ message: 'Không tìm thấy bài viết.' });
  }
  res.json(post);
};
```
Sau đó, trong file chính của ứng dụng (ví dụ: `app.js` hoặc `server.js`), bạn sẽ import và sử dụng controller này:
```js
// app.js (hoặc server.js)
const express = require('express');
const app = express();
const port = 3000;

// Import controller
const postController = require('./controllers/postController');

// Middleware để parse body của request (ví dụ: JSON)
// Điều này rất quan trọng để req.body có dữ liệu khi bạn gửi POST/PUT
app.use(express.json());

// Định nghĩa routes và kết nối với các hàm trong controller
app.get('/', (req, res) => {
  res.send('Chào mừng đến với API của tôi!');
});

app.get('/api/posts', postController.getPosts);
app.post('/api/posts', postController.createPost);
app.get('/api/posts/:id', postController.getPostById); // Route với tham số động :id

app.listen(port, () => {
  console.log(`Server đang chạy tại http://localhost:${port}`);
});
```
Trong ví dụ trên, khi có yêu cầu `GET /api/posts`, Express sẽ gọi hàm `getPosts` từ `postController`. Khi có yêu cầu `POST /api/posts`, nó sẽ gọi `createPost`. Route `/api/posts/:id` là một ví dụ về route có tham số động, nơi `:id` sẽ được trích xuất từ URL và có sẵn trong `req.params.id` bên trong controller.
### Định nghĩa Routes và Controllers theo cấu trúc thư mmục
Để quản lý dự án chuyên nghiệp và dễ uqanr lý hơn, ta thường tách `routes` ra các file riêng biệt, tương tự như `controllers`. Đặc biệt hữu ích khi ta có nhiều loại tài nguyên(users, products, orders, vv), mỗi loại có bộ routes và controllers riêng.
Cấu trúc phổ biến
```
.
├── app.js            // File chính khởi tạo Express app
├── routes/
│   └── postRoutes.js // Định nghĩa routes cho bài viết
│   └── userRoutes.js // Định nghĩa routes cho người dùng
├── controllers/
│   └── postController.js // Logic xử lý cho bài viết
│   └── userController.js // Logic xử lý cho người dùng
└── package.json
```

```js
// routes/postRoutes.js
const express = require('express');
const router = express.Router(); // Dùng express.Router() để tạo một instance router
const postController = require('../controllers/postController');

// Định nghĩa các routes cho bài viết
router.get('/', postController.getPosts); // GET /api/posts
router.post('/', postController.createPost); // POST /api/posts
router.get('/:id', postController.getPostById); // GET /api/posts/:id

// Thêm các route khác cho PUT, DELETE nếu cần
// router.put('/:id', postController.updatePost);
// router.delete('/:id', postController.deletePost);

module.exports = router; // Export router để app.js có thể sử dụng
```

```js
// controllers/postController.js
exports.getPosts = (req, res) => {
  // Logic để lấy danh sách bài viết từ cơ sở dữ liệu (sẽ học sau)
  const posts = [
    { id: 1, title: 'Bài viết 1', content: 'Nội dung bài viết 1' },
    { id: 2, title: 'Bài viết 2', content: 'Nội dung bài viết 2' },
  ];
  res.json(posts);
};

exports.createPost = (req, res) => {
  // Logic để tạo bài viết mới
  const newPost = req.body; // Giả sử dữ liệu bài viết mới nằm trong req.body
  console.log('Tạo bài viết mới:', newPost);
  res.status(201).json({ message: 'Bài viết đã được tạo thành công.', post: newPost });
};

exports.getPostById = (req, res) => {
  const postId = req.params.id; // Lấy ID từ URL
  // Logic để lấy bài viết theo ID từ cơ sở dữ liệu
  const post = { id: postId, title: `Bài viết ${postId}`, content: `Nội dung bài viết ${postId}` };
  if (post.id === '3') { // Ví dụ đơn giản cho trường hợp không tìm thấy
    return res.status(404).json({ message: 'Không tìm thấy bài viết.' });
  }
  res.json(post);
};
```

```js
// app.js
const express = require('express');
const app = express();
const port = 3000;

// Import route modules
const postRoutes = require('./routes/postRoutes');

// Middleware để parse body của request (JSON)
app.use(express.json());

// Routes cơ bản
app.get('/', (req, res) => {
  res.send('Chào mừng đến với API của tôi!');
});

// Gắn các route của postRoutes vào một base path
// Tất cả routes trong postRoutes.js sẽ bắt đầu với /api/posts
app.use('/api/posts', postRoutes);

// Xử lý các route không tồn tại (middleware cuối cùng)
app.use((req, res, next) => {
  res.status(404).json({ message: 'Route không tìm thấy' });
});

// Middleware xử lý lỗi tập trung (sẽ học kỹ hơn sau)
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Có lỗi xảy ra!');
});


app.listen(port, () => {
  console.log(`Server đang chạy tại http://localhost:${port}`);
});
```
Với cấu trúc này, mọi request đến `/api/posts` sẽ được chuyển hướng đến `postRoutes.js`, nơi các route cụ thể (như `/`, `/:id`) sẽ được khớp và xử lý bởi `postController`. Điều này tạo ra một phân cấp rõ ràng, dễ hiểu và dễ mở rộng.
Khi client gửi request, flow xử lý trong Express sẽ diễn ra như sau:
![[Pasted image 20260228163553.png]]
### Các loại tham số trong Request
Khi làm việc với routes và controllers, bạn sẽ thường xuyên cần truy cập vào dữ liệu được gửi kèm trong yêu cầu. Express cung cấp một số cách để làm điều này thông qua đối tượng `req`:
1.  **`req.params` (Route Parameters):**  Sử dụng để lấy các giá trị động từ URL path. Ví dụ, trong route `/api/posts/:id`, `:id` là một route parameter.
```js 
// Route: app.get('/api/posts/:id', postController.getPostById);
// URL: GET /api/posts/123
// Trong controller:
const postId = req.params.id; // postId sẽ là '123'
```
2. **`req.query` (Query String Parameters):** Sử dụng để lấy các tham số sau dấu `?` trong URL. Thường dùng cho việc lọc, phân trang hoặc sắp xếp.
```js
// Route: app.get('/api/posts', postController.getPosts);
// URL: GET /api/posts?category=tech&limit=10
// Trong controller:
const category = req.query.category; // category sẽ là 'tech'
const limit = req.query.limit;       // limit sẽ là '10'
```
3. **`req.body` (Request Body):** Chứa dữ liệu được gửi trong phần body của yêu cầu HTTP (thường với các phương thức POST, PUT, PATCH). Để `req.body` có dữ liệu, bạn cần sử dụng middleware như `express.json()` (để xử lý JSON) hoặc `express.urlencoded()` (để xử lý dữ liệu form).
```js
// Route: app.post('/api/posts', postController.createPost);
// Khi client gửi:
// POST /api/posts
// Content-Type: application/json
// Body: { "title": "Bài viết mới", "content": "Nội dung." }
// Trong controller:
const newPost = req.body; // newPost sẽ là { title: 'Bài viết mới', content: 'Nội dung.' }
```
