#### MODULE INTRODUCTION
-  Module trong JS chỉ là tập hợp các từ (hoặc code, tùy từng trường hợp).
-  Trong js, module có thể là các function, third party, thậm chí là các file.


Các lợi ích khi sử dụng module:

  - Dễ bảo trì: Theo định nghĩa, một module tự đóng gói. Một module được thiết kế tốt nhắm tới việc làm giảm sự phụ thuộc của các phần trong codebase càng nhiều càng tốt để nó có thể phát triển một cách độc lập. Cập nhật một module dễ dàng hơn nhiều khi module đó liên kết lỏng lẻo với các phần code khác.
  - Tính tái sử dụng: Hãy thành thật: chúng ta đều sao chép code mình viết trước đó đến một dự án mới lúc này hay lúc khác. Ví dụ, hãy tưởng tượng bạn sao chép một vài hàm tiện ích bạn viết ở dự án trước cho dự án hiện tại của bạn, ...

#### DATA TYPE + OPERATION
##### DATA TYPE
**1. Primitive types:**
- Undefined    : khi tạo 1 biến mới mà chưa gán giá trị cho nó. 
```sh
var a;  // a có giá trị là undefined
``` 
- Boolean	     : true, false
- Number
- BigInt
- String
- Symbol (ES6) 	

**2. Reference types:**

- Null(Object) : có giá trị là null
- Object       :
```sh
   var myDog = {     
      weight: 10,
      name: 'Lu',
      age: 10,                              // object literal
      eat: function(bone){
          this.weight= this.weight + bone.weight;
      }
    };
```
- Function (object) : 
```sh
  const add = (a, b) => return a + b;     // Arrow function (ES6)

  function Mouse(color, weight){
       this.type = 'Mouse';
       this.color = color;                // Constructor function 
       this.weight = weight;
       }
  
  function addTwo(a, b) {
    return a + b;                         // Normal function
  }

  const talk = function() {
      console.log('Hello everybody');     // Anounymous function 
  }
```

##### OPERATION

| Operator | Description |
| ------ | ------ |
| +  |  Addition |
| -  | Subtraction  |
| *  | Multiplication |
| ** | Exponentiation (ES2016) |
| /  |  Division    |
| %  |  Modulus (Division Remainder)  |
| ++ |  Increment   |
| -- |  Decrement   |


#### SCOPE OF VARIABLES  (lET & CONST & VAR)
- const dùng để khai báo một hằng số - là một giá trị không thay đổi được trong suốt quá trình chạy.
```sh
const A = 5; 
A = 10   // throw Error
```
- let (block scoped) tạo ra một biến chỉ có thể truy cập được trong block bao quanh nó, khác với var (globally scoped) - tạo ra một biến có phạm vi truy cập xuyên suốt function chứa nó.    
```sh
Sử dụng var:

function foo() {
   var x = 10;
   if (true) {
      var x = 20; 
      console.log(x); // 20
   }
   console.log(x); // 20
}

Sử dụng let:

function foo() {
   let x = 10;
   if (true) {
      let x = 20; // 
      console.log(x); // 20
   }
   console.log(x); // 10
}
```

#### STRING & STRING METHODS
##### STRING
-  Đối tượng String là 1 chuổi liên tiếp các kí tự.
-  Có thể viết String trong dấu nháy đơn hoặc nháy kép.
```sh
var carName1 = "Volvo XC60";  // Double quotes
var carName2 = 'Volvo XC60';  // Single quotes
```

##### STRING METHODS
Những string method em thường dùng
- length: trả về độ dài của chuỗi  
```sh
var txt = 'hungdeptrai'
txt.length        // 11
```
- slice(start, end): trả về 1 chuỗi con của string
```sh
var str = "Apple, Banana, Kiwi";
var res = str.slice(7, 13);      // Banana
```
- toUpperCase(), toLowerCase(), concat(), ...
- **Regex**

#### ARRAY & ARRAY METHODS
##### ARRAY
- JavaScript arrays are used to store multiple values in a single variable.
```sh
let cars = ["Saab", "Volvo", "BMW"];
```
##### ARRAY METHODS
Tất cả ví dụ sử dụng arr = [1, 2, 3, 4]
- array.map()
```sh
arr.map(item => {
   return item + 1;            // arr = [2, 3, 4, 5]
 })                      
```
- array.filter()
```sh
arr.filter(item => {
   return (item % 2 == 0);            // arr = [2, 4]
 })                      
```
- array.reduce()
```sh
Không có initValue:
arr.reduce((item1, item2) => {
  return item1 + item2;             // 10 (1 + 2 + 3 + 4)
})


Có initValue:
 var orders = [
  {quantity: 2, unitPrice: 100},
  {quantity: 1, unitPrice: 400},
  {quantity: 5, unitPrice: 15}
];
 orders.reduce((currentTotal, product) => {
  return currentTotal + product.quantity                   // Tính tổng giá tiền 
 },0)
```