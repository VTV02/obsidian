Tương tác với db là phần cốt lỗi của bất kỳ ứng dụng  backend nào. Cần nơi để lưu trữ thông tin lâu dài. Trong `Nodejs` thay vì tương tcs trực tiếp với db bằng các câu lệnh `SQL` hoặc `API DB` chúng ta thường sử dụng một `Object Data Modeling(ODM)` hoặc `Object Relational Mapping(ORM)` library để đơn giản hóa công việc

## Thiết lập MongoDB và Mongoose

Trước khi viết code, bạn cần có một instance MongoDB đang chạy. Bạn có thể cài đặt MongoDB cục bộ, sử dụng Docker, hoặc dễ nhất là dùng một dịch vụ MongoDB đám mây như MongoDB Atlas. Đối với module này, giả sử bạn đã có một database MongoDB sẵn sàng để kết nối.

Để sử dụng Mongoose, chúng ta cần cài đặt nó vào dự án của mình:
```shell
npm install mongoose
```
Sau đó, trong file `app.js` (hoặc `server.js`) của backend, bạn sẽ thiết lập kết nối:
### Load các thư viện
```js
require("dotenv").config();   // Đọc file .env và đưa các biến vào process.env
const express = require("express");  // Framework web cho Node.js
const mongoose = require("mongoose"); // Thư viện kết nối MongoDB

```
`dotenv` : Đọc file `.env` trong thư mục gốc, parse nội dung rồi gán vào object `process.env` , sau dòng này thì `process.env.MONGO_URL` sẽ có giá trị `mongodb+srv://luciferDeveloper:MgDb123456@cluster0.qhr63ij.mongodb.net/?appName=Cluster0` 
`express` : framework giúp tạo web server dễ dàng(xử lý route, request, response,...)
`mongoose`: ODM(Object Data Modeling) giúp kết nối và thao tác với MongoDB bằng Javascript
### Khởi tạo app và cấu hhhình

```js
const app = express();          // Tạo instance Express
const PORT = process.env.PORT || 3000;  // Lấy PORT từ .env, nếu không có thì dùng 3000

const MONGODB_URI =
  process.env.MONGO_URL || "mongodb://localhost:27017/work-database";
  // Lấy URL MongoDB từ .env, nếu không có thì dùng localhost
```
- Nếu `process.env.MONGO_URL` có giá trị thì nó dùng MongDB Atlas trên Cloud ngược lại thì nó sẽ dùng local
### Kết nối MongoDB & Khởi động Server

```js
mongoose
  .connect(MONGODB_URI)       // Kết nối đến MongoDB (trả về Promise)
  .then(() => {               // Nếu kết nối THÀNH CÔNG
    console.log("Connected to MongoDB");
    app.listen(PORT, () => {  // Mới bắt đầu lắng nghe request
      console.log(`Server is running on port ${PORT}`);
    });
  })
  .catch((error) => {         // Nếu kết nối THẤT BẠI
    console.log(error);       // In lỗi ra console
    process.exit(1);          // Tắt app với mã lỗi 1
  });
```

```js
mongoose.connect(URI)
        │
        ├── ✅ Thành công ──→ "Connected to MongoDB"
        │                      │
        │                      └──→ app.listen(3000) ──→ "Server is running on port 3000"
        │                            (Bắt đầu nhận request HTTP)
        │
        └── ❌ Thất bại ──→ In lỗi ──→ process.exit(1) (Tắt app)

```
Tại sao phải để `app.listen` nằm TRONG `then()` Vì phải đảm bảo `database` đã kết nối xong rồi thì mới nhận `request`. Nếu cho `Server` chạy trước khi DB sẵn sàng, các request DB sẽ bị lỗi
### Middleware và Routes

```js
app.use(express.json());  // Middleware: tự động parse body JSON của request

```
Khi `Client`gửi `request` với body dạng `JSON` thì `middleware` sẽ parse và đưa vào `req.body` nếu không có dòng này thì `req.body` sẽ là `undefined` 
```js
app.get("/", (req, res) => {   // Khi có GET request đến "/"
  res.send("Hello World!");    // Trả về text "Hello World!"
});
```
- **`app.get("/")`** = Đăng ký route xử lý **GET** request tại đường dẫn `/`
- **`req`** = object chứa thông tin request (headers, query params, body...)
- **`res`** = object dùng để gửi response về client
### Workflow

```js
1. Node.js chạy app.js
2. dotenv load biến từ .env → process.env
3. Express app được tạo
4. Kết nối MongoDB Atlas
5. Kết nối OK → Server listen port 3000
6. Client gửi GET http://localhost:3000/
7. Express match route "/" → callback chạy
8. res.send("Hello World!") → Client nhận response
```

Ở đây `mongose.connect` là hàm chính để kết nối. Nó trả về một `Promise`, cho phép chúng ta xử lý thành công hay thất bại. Điều quan trọng cần chú ý là chỉ khởi động server Express khi kết nối `database` thành công, vì ứng dụng chúng ta sẽ không hoạt động nếu không có `DB`
```
**Key Takeaway:** Kết nối MongoDB cần được thiết lập sớm trong ứng dụng và đảm bảo thành công trước khi server Express bắt đầu lắng nghe request.
```
### Định nghĩa Schema và Model
MongoDB là CSDL `NoSQL`, document-oriented có nghĩa là nó lưu dữ liệu dưới dạng các document
JSON. Tuy nhiên thì MongoDB lại cấu trúc bằng cách sử dụng `Schema` . `MongoDB schema` định nghĩa cấu trúc của document trng một collection, bao gồm các kiểu dữ liệu, ràng buộc, giá trị mặc định, ...
Khi bạn đã định nghĩa một `Schema` bạn có thể tạo một `Model`. `Model` là một `constructor` để tạo các `instance` của document, và nó cũng là điểm truy cập để tương tác với collection tương ứng trong database(ví dụ, `find()` `save()` `update()` ,...)
Trong code 

app.js của bạn, "instance" nghĩa là **một đối tượng cụ thể được tạo ra từ một class/function**
![[Pasted image 20260301163509.png]]
## Ví dụ đời thực

Giống như **khuôn bánh** vs **chiếc bánh**:
```js
// "express" là khuôn bánh (blueprint)
// "app" là chiếc bánh được đúc ra từ khuôn (instance)
const app = express();

// Bây giờ chiếc bánh (instance) có đầy đủ chức năng:
app.get(...)     // Đăng ký route
app.use(...)     // Thêm middleware
app.listen(...)  // Bắt đầu lắng nghe

```
Bạn **có thể tạo nhiều instance** từ cùng một bản thiết kế:
```js
const app1 = express();  // Instance 1 — chạy port 3000
const app2 = express();  // Instance 2 — chạy port 4000

// Mỗi instance hoạt động ĐỘC LẬP
app1.get("/", (req, res) => res.send("Server 1"));
app2.get("/", (req, res) => res.send("Server 2"));

app1.listen(3000);
app2.listen(4000);
```

```js
require("dotenv").config();
//       ↑ dotenv.config() không tạo instance, nó chỉ chạy hàm config

const express = require("express");
//    ↑ Đây là MODULE (bản thiết kế), chưa phải instance

const mongoose = require("mongoose");
//    ↑ Đây cũng là MODULE — mongoose là singleton (chỉ có 1 instance duy nhất toàn app)

const app = express();
//    ↑ ĐÂY LÀ INSTANCE — một Express app cụ thể được tạo ra
```
**Lưu ý**: `mongoose` hơi đặc biệt — nó là **singleton**, tức là dù bạn `require("mongoose")` ở nhiều file khác nhau, nó luôn trả về **cùng một instance**. Vì vậy bạn chỉ cần `.connect()` một lần trong 
app.js, và mọi file khác đều dùng chung kết nối đó.
### Schema là gì?
Shema = bản thiết kế mô tả cấu trúc dữ liệu sẽ được lưu trong `MongoDB`
Nếu ví dụ `MongoDB` như một cuốn sổ thì:

| ==Khái niệm==        | ==Ví dụ thực tế==               | ==Trong `MongoDB/Mongoose`==              |
| ---------------- | --------------------------- | ------------------------------------- |
| Cuốn sổ          | Cuốn sổ quản lý             | `Database` (work-database)            |
| Trang sổ         | Trang `Danh sách nhân viên` | `Collection` (`product`, `user`, ...) |
| Kẻ cột           | Cột: Tên, Tuổi, Số ĐT       | `Schema` (định nghĩa các field)       |
| Một hàng dữ liệu | Nguyễn Văn A, 25, 09849803  | `Document`(1 `record` )               |
### Mối quan hệ Schema -> Model -> Document
```js
Schema  ──→  Model  ──→  Document
(thiết kế)   (khuôn)    (sản phẩm)
```
### Example deetail

Step1: `Schema` định nghĩa cấu trúc
```js
const mongoose = require("mongoose");

const productSchema = new mongoose.Schema({
  name: {
    type: String,       // Kiểu dữ liệu: chuỗi
    required: true,     // Bắt buộc phải có
  },
  price: {
    type: Number,       // Kiểu dữ liệu: số
    required: true,
    default: 0,         // Nếu không truyền → mặc định = 0
  },
  description: {
    type: String,
    required: false,    // Không bắt buộc
  },
  inStock: {
    type: Boolean,
    default: true,
  },
  createdAt: {
    type: Date,
    default: Date.now,  // Tự động lấy thời điểm tạo
  },
});
```
Schema nói: _"Mỗi sản phẩm PHẢI có `name` (chuỗi) và `price` (số), CÓ THỂ có `description`, `inStock`, `createdAt`"_.

Step 2: `Model` - Tạo `Khuôn` từ Schema 
```js 
mongoose.model("Products", productSchema);
```
- `mongoose.model("Products", productSchema);` tạo `model` tên Product
- Model giống khuôn bánh, dùng để tạo, chỉnh sửa, xóa document
- `MongoDB` tự tạo `collection` tên `products`  
Step 3: `Document` - Tạo dữ liệu thực
```js 
// Tạo 1 sản phẩm mới (document)
const newProduct = new Product({
  name: "iPhone 16",
  price: 25000000,
  description: "Điện thoại Apple",
});

await newProduct.save(); // Lưu vào MongoDB
```
Các kiểu dữ liệu trong `Schema` 
```js
const exampleSchema = new mongoose.Schema({
  title:      String,              // Chuỗi
  count:      Number,              // Số
  isActive:   Boolean,             // true/false
  createdAt:  Date,                // Ngày tháng
  tags:       [String],            // Mảng chuỗi ["tag1", "tag2"]
  metadata:   Object,              // Object tự do
  userId:     mongoose.Schema.Types.ObjectId,  // ID tham chiếu document khác
});
```
### Các option phổ biến của từng trường

```js
const userSchema = new mongoose.Schema({
  email: {
    type: String,
    required: [true, "Email là bắt buộc"],  // Bắt buộc + thông báo lỗi tùy chỉnh
    unique: true,       // Không cho trùng
    trim: true,         // Tự xóa khoảng trắng thừa 2 đầu
    lowercase: true,    // Tự chuyển thành chữ thường
  },
  age: {
    type: Number,
    min: [0, "Tuổi không âm"],     // Giá trị tối thiểu
    max: [150, "Tuổi quá lớn"],    // Giá trị tối đa
  },
  role: {
    type: String,
    enum: ["user", "admin", "moderator"],  // Chỉ chấp nhận các giá trị này
    default: "user",
  },
});
```
### Cấu trúc thư mục khuyến nnghị

```js
work-database/
├── app.js              ← Entry point
├── models/             ← Chứa Schema + Model
│   └── product.model.js
├── routes/             ← Định nghĩa route
│   └── product.route.js
├── controllers/        ← Logic xử lý
│   └── product.controller.js
├── .env
└── package.json
```

```
Schema → Mô tả cấu trúc dữ liệu (trường nào, kiểu gì, bắt buộc không...)
Model  → Tạo từ Schema, dùng để thao tác CRUD với MongoDB
Document → Một bản ghi cụ thể trong database
```
**Ví dụ file `models/product.model.js`:**
```js
const mongoose = require("mongoose");

const productSchema = new mongoose.Schema(
  {
    name:        { type: String, required: true },
    price:       { type: Number, required: true },
    description: { type: String },
    inStock:     { type: Boolean, default: true },
  },
  {
    timestamps: true,  // Tự tạo createdAt + updatedAt
  }
);

module.exports = mongoose.model("Product", productSchema);

```
**Sử dụng trong controller:** 
```js
const Product = require("../models/product.model");

// Tạo mới
const product = await Product.create({ name: "Laptop", price: 15000000 });

// Lấy tất cả
const products = await Product.find();

// Tìm theo ID
const one = await Product.findById("abc123");

// Cập nhật
await Product.findByIdAndUpdate("abc123", { price: 20000000 });

// Xóa
await Product.findByIdAndDelete("abc123");

```


### **Kiến trúc MVC**

Dự án được tổ chức theo mô hình MVC (Model - View - Controller), giúp tách biệt các concern và dễ bảo trì:

●      Model (models/Post.js): Định nghĩa cấu trúc dữ liệu và tương tác với database

●      Controller (controllers/postController.js): Xử lý logic nghiệp vụ cho từng API endpoint

●      Routes (routes/postRoutes.js): Định nghĩa URL endpoints và ánh xạ đến controller tương ứng

●      App (app.js): File entry point — khởi tạo server, kết nối DB, đăng ký middleware và routes

Sẽ có ít nhất 3 thành phần
- model folder : nơi mà Schema sẽ được tạo, cái cấu trúc nằm ở đây
- controller: nơi sẽ xử lý logic như `POST, PUT, ....`
- routes: nới sẽ xử lý điều hướng tương ứng đến các controller
Cụ thể như sau
```js 
// models/Post.js
//import thư viện ODM giúp tương tác với MongoDB bằng Javascript Objects
const mongoose = require("mongoose");
// Định nghĩa Schema cho bài viết
//Tạo Schema(bản thiết kế) cho document trong MongoDBMongoDB
const postSchema = new mongoose.Schema({
  title: {

    type: String,

    required: [true, "Tiêu đề bài viết không được để trống."], // title là bắt buộc

    trim: true, // Xóa khoảng trắng ở đầu và cuối

    minlength: [5, "Tiêu đề phải có ít nhất 5 ký tự."],

    maxlength: [100, "Tiêu đề không được vượt quá 100 ký tự."],

  },

  content: {

    type: String,

    required: [true, "Nội dung bài viết không được để trống."],

  },

  author: {

    type: String,

    default: "Anonymous", // Mặc định là 'Anonymous' nếu không được cung cấp

    trim: true,

  },

  tags: [String], // Mảng các chuỗi, ví dụ: ['nodejs', 'express', 'mongodb']

  createdAt: {

    type: Date,

    default: Date.now, // Tự động điền thời gian tạo

  },

  updatedAt: {

    type: Date,

    default: Date.now, // Tự động điền thời gian cập nhật

  },

});
// Trước khi lưu (save) tài liệu, cập nhật trường 'updatedAt'
postSchema.pre("save", function () {
  this.updatedAt = Date.now();
});
// Tạo Model từ Schema liên kết với collection 'posts' trong MongoDB(Mongoose sẽ 
//tự chuyển thành chữ thường và thêm 's')
const Post = mongoose.model("Post", postSchema);
module.exports = Post;
```
Sau khi đã có `Schema` và `Model` để làm việc với DB
Ta cần xử lý logic nghiệp vụ cho từng API endpoint mỗi hàm sẽ nhận `req` và `res` từ `Express` 
![[Pasted image 20260302144531.png]]

```js
// controllers/postController.js
//Import cái Model mới được tạo
const Post = require("../models/Post"); // Import Post Model

// 1. Lấy tất cả bài viết
exports.getAllPosts = async (req, res) => {

  try {
    const posts = await Post.find(); // Tìm tất cả bài viết trong DB
    res.status(200).json({
      status: "success",
      results: posts.length, // Số lượng bài viết trả về
      data: {
        posts, // Dữ liệu bài viết
      },
    });
  } catch (err) {

    res.status(500).json({

      status: "error",

      message: err.message || "Lỗi khi lấy danh sách bài viết.",

    });

  }

};

// 2. Lấy một bài viết theo ID

exports.getPostById = async (req, res) => {

  try {

    const post = await Post.findById(req.params.id); // Tìm bài viết theo ID từ URL params
    if (!post) {
      return res.status(404).json({
        status: "fail",
        message: "Không tìm thấy bài viết với ID này.",
      });
    }
    res.status(200).json({
      status: "success",
      data: {
        post,
      },
    });

  } catch (err) {
    // Xử lý lỗi nếu ID không hợp lệ (ví dụ: định dạng sai)
    if (err.name === "CastError") {

      return res.status(400).json({

        status: "fail",

        message: "ID bài viết không hợp lệ.",

      });

    }

    res.status(500).json({

      status: "error",

      message: err.message || "Lỗi khi lấy bài viết.",

    });

  }

};
// 3. Tạo bài viết mới
exports.createPost = async (req, res) => {

  try {

    // Dữ liệu bài viết mới được gửi trong body của request
    const newPost = await Post.create(req.body);
    res.status(201).json({
      // Mã 201 Created cho biết tài nguyên đã được tạo thành công
      status: "success",
      data: {
        post: newPost,
      },
    });

  } catch (err) {

    // Xử lý lỗi validator của Mongoose (ví dụ: thiếu trường required)
    if (err.name === "ValidationError") {
      const errors = Object.values(err.errors).map((el) => el.message);
      return res.status(400).json({
        status: "fail",
        message: errors.join(". "),
      });
    }
    res.status(500).json({
      status: "error",
      message: err.message || "Lỗi khi tạo bài viết mới.",
    });
  }
};
// 4. Cập nhật bài viết
exports.updatePost = async (req, res) => {
  try {
    // `findByIdAndUpdate` nhận 3 tham số: ID, dữ liệu cần cập nhật, và options
    const post = await Post.findByIdAndUpdate(req.params.id, req.body, {
      new: true, // Trả về tài liệu đã được cập nhật thay vì tài liệu gốc
      runValidators: true, // Chạy các validator đã định nghĩa trong schema
    });
    if (!post) {
      return res.status(404).json({
        status: "fail",
        message: "Không tìm thấy bài viết để cập nhật.",
      });
    }
    res.status(200).json({
      status: "success",
      data: {
        post,
      },
    });

  } catch (err) {

    if (err.name === "CastError") {

      return res.status(400).json({

        status: "fail",

        message: "ID bài viết không hợp lệ.",

      });

    }

    if (err.name === "ValidationError") {

      const errors = Object.values(err.errors).map((el) => el.message);

      return res.status(400).json({

        status: "fail",

        message: errors.join(". "),

      });

    }

    res.status(500).json({

      status: "error",

      message: err.message || "Lỗi khi cập nhật bài viết.",

    });

  }

};

// 5. Xóa bài viết
exports.deletePost = async (req, res) => {

  try {

    const post = await Post.findByIdAndDelete(req.params.id);
    if (!post) {
      return res.status(404).json({
        status: "fail",
        message: "Không tìm thấy bài viết để xóa.",
      });
    }
    // Mã 204 No Content cho biết yêu cầu đã thành công nhưng không có nội dung nào được trả về
    res.status(204).json({
      status: "success",
      data: null, // Dữ liệu trả về là null
    });

  } catch (err) {

    if (err.name === "CastError") {

      return res.status(400).json({

        status: "fail",

        message: "ID bài viết không hợp lệ.",

      });

    }

    res.status(500).json({

      status: "error",

      message: err.message || "Lỗi khi xóa bài viết.",

    });

  }
};
```
Sau khi đã viết xong Xử lý logic cho từng API endpoint thì tiếp theo ta cần phải xác định được tuyến đường nào để sử dụng hàm controller tương ứng
```js
// routes/postRoutes.js
const express = require("express");
const postController = require("../controllers/postController"); // Import controller
const router = express.Router(); // Tạo một router mới
// Định nghĩa các routes cho tài nguyên 'posts'
router
  .route("/") // Áp dụng cho '/api/posts'
  .get(postController.getAllPosts) // GET /api/posts
  .post(postController.createPost); // POST /api/posts
router
  .route("/:id") // Áp dụng cho '/api/posts/:id'
  .get(postController.getPostById) // GET /api/posts/:id
  .put(postController.updatePost) // PUT /api/posts/:id
  .delete(postController.deletePost); // DELETE /api/posts/:id
module.exports = router;
```
Sau khi mọi thứ đã sẵn sàng thì ta phải kết nối đến `Databse và chạy server`
```js
// app.js (hoặc server.js)
const express = require("express");
const morgan = require("morgan"); // Middleware để log request
const dotenv = require("dotenv"); // Để quản lý biến môi trường
const mongoose = require("mongoose"); // Mongoose để kết nối MongoDB

dotenv.config({ path: "./config.env" }); // Nạp biến môi trường
const app = express();
// --- Kết nối MongoDB ---

const DB = process.env.DATABASE;
mongoose
  .connect(DB)
  .then(() => console.log("DB connection successful!"))
  .catch((err) => console.error("DB connection error:", err));
// --- Middleware ---

if (process.env.NODE_ENV === "development") {
  app.use(morgan("dev")); // Chỉ dùng morgan ở chế độ development
}

app.use(express.json()); // Body parser: đọc dữ liệu JSON từ body của request

app.use(express.static(`${__dirname}/public`)); // Phục vụ các file tĩnh (nếu có)

// --- Routes ---

const postRoutes = require("./routes/postRoutes"); // Import postRoutes

app.use("/api/posts", postRoutes); // Mount postRoutes lên đường dẫn '/api/posts'

// Xử lý các route không tồn tại (404 Not Found)

app.use((req, res) => {

  res.status(404).json({

    status: "fail",

    message: `Không tìm thấy đường dẫn: ${req.originalUrl}`,

  });

});
// --- Start Server ---
const port = process.env.PORT || 3000;

app.listen(port, () => {

  console.log(`App running on port ${port}...`);

});
```
Cần có file `config.env` file này chứa các cấu hình `PORT` `DATABASE` dữ liệu nhạy cảm KO ĐƯỢC PUSH LÊN GITHUB
```js
NODE_ENV=development

PORT=3000

DATABASE=mongodb+srv://luciferDeveloper:MgDb123456@cluster0.qhr63ij.mongodb.net/?appName=Cluster0
```
