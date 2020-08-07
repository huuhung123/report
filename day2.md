#### LOOPS

- Các vòng lặp có thể thực thi một khối mã nhiều lần.
- Vòng lặp rất tiện dụng, nếu muốn chạy cùng một mã nhiều lần, mỗi lần có một giá trị khác nhau.

```sh
Không dùng vòng lặp:
text += cars[0] + "<br>";
text += cars[1] + "<br>";
text += cars[2] + "<br>";
text += cars[3] + "<br>";
text += cars[4] + "<br>";
text += cars[5] + "<br>";

Dùng vòng lặp:
for (let i = 0; i < cars.length; i++) {
  text += cars[i] + "<br>";
}
```

#### UNDERSTANDING FUNCTIONS AND ARROW FUNCTIONS

##### FUNCTIONS

- Hàm JavaScript là một khối mã được thiết kế để thực hiện một tác vụ cụ thể.

```sh
Syntax:
function name(parameter1, parameter2, parameter3) {
  // code to be executed
}

Ex:
function addTwoNumbers(p1, p2) {
  return p1 + p2;   // The function returns add two numbers
}
```

- Có nhiều loại function:

```sh
const add = (a, b) => return a + b;     // Arrow function (ES6)

function Mouse(color, weight){
    this.type = 'Mouse';
    this.color = color;                 // Constructor function
    this.weight = weight;
  }

function addTwo(a, b) {
    return a + b;                       // Normal function
  }

const talk = function() {
    console.log('Hello everybody');     // Anounymous function
}
```

##### ARROW FUNCTION (ES6)

- Arrow function được giới thiệu trong ES6.
- Arrow function cho phép chúng ta viết cú pháp hàm ngắn hơn.

```sh
Dùng nomal function:
add = function(a ,b) => {
  return a + b;
}

Dùng Arrow function:
const add = (a, b) => {
    return a + b;                OR           const add = (a, b) => a + b
}
```

#### OBJECTS, PROPERTIES & METHODS

- Một đối tượng trong JS là một danh sách các item, mỗi item là một cặp name-value, trong đó value có thể là: các kiểu dữ liệu cơ bản, function, hay cũng có thể là một object khác (kiểu dữ liệu phức hợp).
- Ta gọi mỗi item là một property(thuộc tính) của object nếu value của item đó có kiểu dữ liệu là kiểu phức hợp hoặc các kiểu dữ liệu cơ bản, ngược lại nếu value của item nó là một hàm (một function) thì ta gọi nó là method của object (phương thức của object).

```sh
const myDog = {     // object literal
    weight: 5,
    name: 'Dan',
    age: 1,
    bark: function(){  //anounymous function
        console.log('Meo meo, my name is', this.name);
    },
    eat: function(bone){
        this.weight= this.weight + bone.weight;
    }
  };

const bone={ weight: 0.5};
console.log('Before eating', myDog.weight);    // Before eating 5
myDog.eat(bone);
console.log('After eating', myDog.weight);     // After eating 5.5

Trong vd trên object có tên là mydog properties là weight, name, age, methods là bark và eat
```

#### ASYNC CODE & PROMISES

##### ASYNC CODE

- JavaScript là ngôn ngữ đơn luồng (single threaded) đồng bộ (synchronous, nhờ vào môi trường browser và nodejs, JavaScript có thể chạy được bất đồng bộ (asynchronous), đa luồng (mutiple threaded).
- Synchronous có nghĩa là xử lý đồng bộ, chương trình sẽ chạy theo từng bước và chỉ khi nào bước 1 thực hiện xong thì mới nhảy sang bước 2, khi nào chương trình này chạy xong mới nhảy qua chương trình khác.
- Ngược lại với Synchronous thì Asynchronous là xử lý bất động bộ, nghĩa là chương trình có thể nhảy đi bỏ qua một bước nào đó.

```sh
Ví dụ về synchronous:
const fs = require('fs');
const text = fs.readFileSync('./song-1.txt', {encoding: 'utf8'});
console.log(text);
fs.writeFileSync('./song-2.txt', text);

Ví dụ về asynchronous:
const fs = require('fs');
fs.readFile('./song-1.txt, {encoding: 'utf8}, (err, data) => {
  fs.writeFile('./song-2.txt', data, err => console.log(err))
})
```

##### PROMISES

- Callback có rất nhiều nhược điểm. Khi ta có nhiều thao tác bất đồng bộ, các callback phải chờ nhau thực hiện, thời gian để hoàn thành sẽ bị kéo dài hơn. Ngoài ra, việc viết các callback lồng nhau cũng làm cho mã nguồn của ta rắc rối và khó bảo trì (callback-hell).
- Vì thế, trong phiên bản ES6 , JavaScript đã được bổ xung thêm ( .then() ) Promise. Nó là một thay thế tuyệt vời cho callbacks và hầu hết cộng đồng nhanh chóng chuyển sang sử dụng nó để thay thế cho callbacks. Code mới của chúng ta gần giống với code cũ, kết quả là trông dễ theo dõi và bảo trì hơn.

```sh
Ví dụ trên sử dụng promise:
const = readFilePromise(path) {
  return new Promise((resolve, reject) => {
    fs.readFile(path, {encoding: 'utf8'}, (err, data) => {
      if(err) {
        reject(err)
      }
      else {
        resolve(data)
      }
    })
  })
}

const = writeFilePromise(path, data) {
  return new Promise((resolve, reject) => {
    fs.writeFile(path, data, (err) => {
      if(err) {
        reject(err)
      }
      else {
        resolve("Successfully")
      }
    })
  })
}

readFilePromise('song1.txt')
  .then(data => writeFilePromise('song2.txt', data))
  .then(result => console.log(result))
  .catch(err => console.log(err))
```

#### EXERCISES

```sh
const convertToRoman = (num) => {
  const roman = {
    M: 1000,
    CM: 900,
    D: 500,
    CD: 400,
    C: 100,
    XC: 90,
    L: 50,
    XL: 40,
    X: 10,
    IX: 9,
    V: 5,
    IV: 4,
    I: 1
  };
  let str = '';
  for (let i of Object.keys(roman)) {
    var q = Math.floor(num / roman[i]);
    num -= q * roman[i];
    str += i.repeat(q);
  }
  return str;
}
```
