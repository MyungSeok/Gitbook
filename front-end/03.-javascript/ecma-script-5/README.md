---
description: 자바스크립트의 ECMA
---

# 02. ECMA Script 5

## Inheritance

자바스크립트에는 자바와 달리 `class` 가 존재하지 않아 `prototype` 을 사용하여 class 를 구현합니다.

#### 상속 Class 생성 

```javascript
function Shape() {
    this.x = 0;
    this.y = 0;
}

Shape.prototype.move = function (x, y) {
    this.x += x;
    this.y += y;
}

function Rectangle() {
    Shape.call(this);
}

Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle; 
```

#### 상속 객체 생성

```javascript
var rect = new Rectangle();

console.log(rect instanceof Rectangle);
console.log(rect instanceof Shape);

rect.move(1, 1);
```

