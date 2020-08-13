## USING EXPRESS ROUTER

## HTML CODE

## REST FULL API

## OOP IN JAVASCRIPT

**FUNCTION CONSTRUCTOR**

```sh
function Mouse(name) {
    this.name = name;
}
Mouse.prototype.run = function() {
    console.log(`${this.name} is running`);
}
const mouse = new Mouse('MicKey');
```

**CLASS**

```sh
class Mouse {
    constructor(name) {
         this.name = name;
    }
    run() {
        console.log(`${this.name} is running`);
    }
}
mouse.run();
```

**INHERITANCE**

```sh
class Animal {
    constructor(name) {
        this.name = name;
    }

    eat() {
        console.log('Eating...');
    }
}

class Bird extends Animal {
    fly() {
        console.log('Flying...');
    }
}
class Parrot extends Bird {
    speak() {
        console.log('Speaking...';)
    }
}

const bird = new Parrot('Vet');
bird.speak();
```

**SUPER**

Từ khóa super được sử dụng để gọi các hàm trên đối tượng cha.

SYNTAX:

```sh
super([arguments]); // gọi hàm khởi tạo cha.
super.functionOnParent([arguments]);
```

EX:

```sh
class Polygon {
  constructor(height, width) {
    this.name = 'Polygon';
    this.height = height;
    this.width = width;
  }
  sayName() {
    console.log('Hi, I am a ', this.name + '.');
  }
}

class Square extends Polygon {
  constructor(length) {
    this.height; // ReferenceError, super needs to be called first!

    // Here, it calls the parent class' constructor with lengths
    // provided for the Polygon's width and height
    super(length, length);

    // Note: In derived classes, super() must be called before you
    // can use 'this'. Leaving this out will cause a reference error.
    this.name = 'Square';
  }

  get area() {
    return this.height * this.width;
  }

  set area(value) {
    this.area = value;
  }
}
```
