### REQUEST - RESPONSE MODEL

### MONGODB
#### QUERY
**Insert**
```sh
Syntax: db.<collection>.insertOne(Many)(data)

Ex:
db.shopping.insertOne({
    name: 'Telephone',
    customer: {
        name: 'Hoang',
        email: 'hoang.nguyen1308@hcmut.edu.vn'
    }
})

db.shopping.insertMany([
    {
    name: 'Laptop',
    customer: {
        name: 'Hieu',
        email: 'hieu123@gmail.com'
        }
    },
    {
    name: 'Laptop',
    customer: {
        name: 'Hoa',
        email: 'hoa.vo1405@hcmut.edu.vn'
        }
    }
])
```
**Update**
```sh
Syntax: db.<collection>.method (<query>, <update>, <option>)
Trong đó: method gồm: update(), updateOne(), updateMany()
          update gồm nhiều phương thức: $set, $unset, $rename, ...

Ex: 
db.shopping.update(
    { index: 1},
    {
        $set: {
            customer: {
                name: 'Hung',
                email: 'dupbolun2012@gmail.com'
            }
        }
    }
)
```
**Delete**
```sh
Syntax: db.<collection>.method(<query>, <option>)
Trong đó: method gồm: remove(), deleteOne(), deleteMany()

Ex:
db.shopping.deleteOne({"customer.name": "Hoa"})
db.shopping.deleteMany({})      // Xóa tất cả


```
#### INDEX
Index sẽ cải thiện tốc độ truy vấn trong mongoDB (quản lí index bằng cây B-tree). Nếu không có index, mongoDB sẽ scan toàn bộ dữ liệu, do đó thời gian sẽ lâu hơn.
Trong mongoDB, index _id là mặc định và là duy nhất trong mỗi collection.
Các thao tác với index trong mongoDB:
- getIndexes(): trả về danh các các index trong collection hiện tại
```sh
Ex:
db.shopping.getIndexes()     
->  [
    {
        "v": 2,
        "key": {
            "_id": 1
        },
        "name": "_id_",
        "ns": "myDb.shopping"
    }
]
```
- createIndex({keyname: [-1 | 1]},  options): Tạo mới index   
Trong đó: 1: ascending, -1: descending
          options:  name, unique, ....
```sh
EX:
db.shopping.createIndex(
    { index: 1 },
    { unique: true }
)
```
- dopIndex({<fieldName>: 1}): xóa 1 index,  dopIndexes(): xóa tất cả index có trong collection
#### AGGREGATE
- Phương thức trong mongoDB giúp thao tác cùng 1 lúc nhiều query (stage) trên tập dữ liệu.
```sh
SYNTAX:
db.<collection>.aggregate([
    <stage1>,
    <stage2>,
    ...
    <stageN>
])
Trong đó: Aggregation Stages bao gồm: $match, $group, $project, $out, ...

Ex:****
db.shopping.aggregate([
    {
        $group: {****
            _id: "$name",
            count: { $sum: 1 }
        }
    }
])

db.shopping.aggregate([
    {$match: { name: "Laptop" }},
    {$group: {_id: "$customer.name"}
])
```
### KHÓ KHĂN VÀ CÁCH KHẮC PHỤC
#### KHÓ KHĂN
- Kiến thức nhiều, ít có tài liệu Tiếng Việt.
- Thao tác với CLI là chủ yếu.
#### CÁCH KHẮC PHỤC
- Luyện tập nhiều, giải vài tập trên mạng

### LINK THAM KHẢO
[QUEY](https://www.tutorialspoint.com/mongodb/index.htm)

[AGGRERATION - 1](https://studio3t.com/knowledge-base/articles/mongodb-aggregation-framework/)

[AGGRERATION - 2](https://www.youtube.com/watch?v=A3jvoE0jGdE&list=PLWkguCWKqN9OwcbdYm4nUIXnA2IoXX0LI&index=1)