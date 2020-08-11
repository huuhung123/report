### HOW THE WEB WORKS

### UNDERSTANDING REQUESTS

### SENDING RESPONSES

### UNDERSTAND NPM - INSTALL 3RD PARTY PACKAGE

### NODEMON

### RELATIONSHIPS IN MONGODB

Relationship trong MongoDB tượng trưng cho cách các Document có mối liên quan với nhau. Relationship có thể được mô hình hóa thông qua phương thức Embeded và Referenced. Những Relationship này có thể là 1:1, 1:N, N:1, hoặc N:N. Dưới đây là ví dụ về đơn giản về relationship trong MongoDB.

EX : Ta có 3 bảng dữ liệu dưới đây:

| ID  | user_id | profession |
| --- | ------- | ---------- |
| 10  | 1       | banking    |
| 11  | 1       | finance    |
| 12  | 1       | trader     |

| ID  | user_id | model | year |
| --- | ------- | ----- | ---- |
| 20  | 1       | BMW   | 1973 |
| 21  | 1       | Lexus | 1965 |

| ID  | name | cell       | city |
| --- | ---- | ---------- | ---- |
| 1   | Hung | 0905683258 | DN   |

Khi dùng relationship trong mongoDB, ta sẽ có document sau:

```sh
{
    _id: ObjectID('AAA'),
    name: "Hung",
    cell: "0905683258",
    city: "DN",
    cars: [
        {
            model: "BMW",
            year: 1973
        },
        {
            model: "Lexus",
            year: 1965
        }
    ],
    professions: ["banking", "finance", "trader"]
}
```

#### EMBEDDING VS REFERRENCING

**EMBEDDING**

```sh
{
    _id: ObjectId('AAA'),
    name: "Hieu",
    addresses: [
        ObjectId('BBB')
        {
            street: "Lac Long Quan",
            city: "HCM",
            country: "VN"
        },
        {
            street: "Au Co",
            city: "Da Nang",
            country: "VN"
        }
    ]
}

```

**REFERRENCING**

```sh
{                                             {
    _id: ObjectID('BBB'),                       _id: ObjectID('CCC'),
    name: "Hieu",                               street: "Lac Long Quan",
    addresses: [                                city: "HCM",
        ObjectID('CCC'),                        country: "VN"
        ObjectID('DDD')                       }
    ]
}                                             {
                                                _id: ObjectID('DDD'),
                                                street: "Au Co",
                                                city: "Da Nang",
                                                country: "VN"
                                              }
```

#### TYPES OF RELATIONSHIPS

**ONE TO ONE**

Ex: Một người đều chỉ có 1 địa chỉ thường trú

```sh
{
   _id: "joe",
   name: "Joe Bookreader",
   address: {
              street: "123 Fake Street",
              city: "Faketon",
              state: "MA",
              zip: "12345"
            }
}
```

**ONE TO MANY**

Ex: Một người có thể có nhiều khóa học khác nhau

```sh
{
   _id: "Tony",
   name: "Tony Stark",
   courses: [
       {
        id_course: "aaa",
        name: "ReactJS",
        date: "11/8/2020",
       },
       {
        id_course: "bbb",
        name: "nodeJS",
        date: "12/8/2020"
       }
   ]
}
```

**MANY TO MANY**

Ex: Một người có nhiều nhiệm vụ khác nhau, một nhiệm vụ có thể có nhiều người học

```sh
{                                   {
    _id: "AAF1",                        _id: ObjectId("AE02"),
    name: "John",                       description: "Write plan",
    tasks: [                            owner: ObjectId("AAF1")
        ObjectId("ADF9"),           }
        ObjectId("AE02"),           {
        ObjectId("AF07")                _id: ObjectId("AF07"),
    ]                                    description: "Read plan",
}                                        owner: ObjectId("AAF1")
                                    }
```

### LINK THAM KHẢO

[RELATIONSHIPS - 1](https://www.youtube.com/watch?v=leNCfU5SYR8)

[RELATIONSHIPS - 2](https://docs.mongodb.com/manual/tutorial/model-referenced-one-to-many-relationships-between-documents/)
