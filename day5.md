### EXPRESS

### MIDDLEWARE IN THIRD PARTY

### HANDLING DIFFERENT ROUTE

### USING EXPRESS ROUTER

### APP NODE + EXPRESS RUN

**B1. Cài đặt Node.js**
**B2. Tạo thư mục project**

```sh
mkdir myapp
cd myapp
```

**B3. Tạo project và kết nối đến npm**

- npm là viết tắt của Node Package Manager, là nơi đặt tất cả các package của node. Package có thể xem như tập các gói code, như module, thực hiện các chức năng chuyên biệt.
- Chạy câu lệnh sau để tạo project:

```sh
npm init
entry point: app.js
```

**B4. Install Express trong thư mục myapp**

- Vẫn trong thư mục myapp, chạy:

```sh
npm install --save express
```

**B5. Khởi chạy text editor và tạo một file tên app.js**

```sh
const express = require('express');
const app = express();
app.get('/', (req, res) => {
  res.send('Hello World!');
});
app.listen(3000, () => {
  console.log('Example app listening on port 3000!');
});
```

**B6. Run App**
Chạy command:

```sh
node app.js
```

Sau khi chạy command, load http://localhost:3000/ trên browser vầ xem kết quả.

Cấu trúc thư mục myApp sẽ bao gồm:

- app.js
- package.js
- node_modules
