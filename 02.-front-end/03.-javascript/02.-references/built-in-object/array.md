# Array

## slice

### Description

배열의 일정 부분을 반환 합니다.

### Syntax

```javascript
arrayObj.slice(start, [end])
```

#### Parameter

* arrayObj
  * **Array** 객체 
* start
  * arrayObject 에 대한 지정된 부분의 시작
* end
  * arrayObject 에 대한 지정된 부분의 끝

### Example

{% tabs %}
{% tab title="Case 1" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(1)
// ['e', 'l', 'l', 'o']
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(1, 4)
// ['e', 'l', 'l']
```
{% endtab %}

{% tab title="Case 3" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(0, -1)
// ['H', 'e', 'l', 'l']
```
{% endtab %}

{% tab title="Case 4" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(-1, 0)
// []
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
이 메소드는 배열의 길이를 변하게 합니다.
{% endhint %}

## shift

### Description

배열의 첫번째 요소를 제거하고, 제거된 요소를 반환합니다.

### Syntax

```javascript
arrayObj.shift()
```

### Example

{% tabs %}
{% tab title="Case 1" %}
```javascript
var arrayObj = ['H', 'e', 'l', 'l', 'o'];

var shifted = arrayObj.shift();

console.log(shifted);
// 'H'

console.log(arrayObj);
// ['e', 'l', 'l', 'o']
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
이 메소드는 배열의 길이를 변하게 합니다.
{% endhint %}

## map

### Description

`map()` 메소드는 배열내의 모든 요소에 대하여 제공된 함수\(callback\)를 호출하고, 그 결과를 모아서 _**새로운 배열을 반환**_ 합니다.

### Syntax

```javascript
var newAry = arrayObj.map(function callback(currentValue[, index[, array]]) {
    // newAry 의 새 요소를 반환
}[, thisArg]);
```

#### Parameter

* callback
  * 새로운 배열 요소를 생성하는 함수
* currentValue
  * 배열 요소 중 현재 처리되고 있는 요소
* index
  * 현재 처리되는 요소의 배열 내 인덱스
* array
  * `map` 메소드가 적용되는 본래의 배열
* thisArg
  * `callback`을 실행할 때 `this`로 사용되는 값 \(기본값은 window 객체\)

### Example

{% tabs %}
{% tab title="Case 1" %}
```javascript
var numbers = [1, 4, 9];
var roots = numbers.map(Math.sqrt);

console.log(numbers);
// [1, 4, 9]

console.log(roots);
// [1, 2, 3]
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
var numbers = [1, 4, 9];
var doubles = numbers.map(function (num) {
    return num * 2;
});

console.log(doubles);
// [2, 8, 18]
```
{% endtab %}

{% tab title="Case 3" %}
```javascript
var mapAry = [{key: 1, value, 10}, {key: 2, value: 20}, {key: 3, value: 30}];
var new_mapAry = mapAry.map(function (obj) {
    var new_obj = {}
    new_obj[obj.key] = obj.value;
    return new_obj;
});

console.log(new_mapAry);
// [{1:10}, {2:20}, {3:30}]
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
이 메소드는 배열의 요소를 변하게 합니다.
{% endhint %}

## filter

### Description

`filter()` 메소드는 배열내의 모든 요소에 대하여 제공된 테스트 함수\(callback\)를 호출하고, 그 결과를 모아서 _**새로운 배열을 반환**_ 합니다.

### Syntax

```javascript
var newAry = arrayObj.filter(function callback(currentValue[, index[, array]]) {
    // 반환형이 boolean 값 true 이면 값이 유지, false 이면 값 삭제
}[, thisArg]);
```

#### Parameter

* callback
  * 새로운 배열 요소를 생성하는 함수
* currentValue
  * 배열 요소 중 현재 처리되고 있는 요소
* index
  * 현재 처리되는 요소의 배열 내 인덱스
* array
  * `map` 메소드가 적용되는 본래의 배열
* thisArg
  * `callback`을 실행할 때 `this`로 사용되는 값 \(기본값은 window 객체\)

### Example

{% tabs %}
{% tab title="Case 1" %}
```javascript
function isBigEnough(value) {
    return value >= 10;
}

var filterd = [12, 5, 8, 130, 44].filter(isBigEnough);

console.log(filtered);
// [12, 130, 44]
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
이 메소드는 배열의 길이를 변하게 합니다.
{% endhint %}

## forEach

### Description

`forEach()` 메소드는 배열 요소마다 한 번씩 제공된 함수\(callback\) 함수를 호출해서 사용합니다.

### Syntax

```javascript
arrayObj.forEach(function callback(currentValue[, index[, array]]) {
    // 반환형 없이 각 요소마다 함수를 실행
}[, thisArg]);
```

#### Parameter

* callback
  * 새로운 배열 요소를 생성하는 함수
* currentValue
  * 배열 요소 중 현재 처리되고 있는 요소
* index
  * 현재 처리되는 요소의 배열 내 인덱스
* array
  * `map` 메소드가 적용되는 본래의 배열
* thisArg
  * `callback`을 실행할 때 `this`로 사용되는 값 \(기본값은 window 객체\)

## sort

### Description

`sort()` 메서드는 배열의 요소를 적절한 위치에 정렬하고 배열을 반환합니다.  
기본 정렬 순서는 _**유니 코드 포인트**_에 따릅니다.

### Syntax

```javascript
arrayObj.sort([compareFunction])
```

#### Parameter

* compareFunction
  * 정렬 순서를 정의하는 함수를 지정합니다. \(미 지정시 기본 정렬 순서에 따름\)

### Example

{% tabs %}
{% tab title="문자 정렬" %}
```javascript
var fruit = ['orange', 'apple', 'banana'];

console.log(fruit.sort());
// ['apple', 'banana', 'orange']
```
{% endtab %}

{% tab title="숫자 정렬" %}
```javascript
var score = [4, 11, 2, 10, 3, 1];

// ASCII 문자 순서로 정렬되어 숫자의 크기대로 나오지 않음
// [1, 10, 11, 2, 3, 4]
score.sort();

// 오름차순 정렬
// [1, 2, 3, 4, 10, 11]
score.sort(function () {
    return a - b;
});

// 내림차순 정렬
// [11, 10, 4, 3, 2, 1] 
score.sort(function () {
    return b - a;
});

```
{% endtab %}

{% tab title="객체 정렬" %}
```javascript
var student = {
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: 45 },
  { name: 'The', value: -12 },
  { name: 'Magnetic' },
  { name: 'Zeros', value: 37 }
};

// value 기준으로 정렬
student.sort(function (a, b) {
  if (a.value > b.value) {
    return 1;
  }
  if (a.value < b.value) {
    return -1;
  }
  // a must be equal to b
  return 0;
});

// name 기준으로 정렬
student.sort(function(a, b) {
  var nameA = a.name.toUpperCase(); // ignore upper and lowercase
  var nameB = b.name.toUpperCase(); // ignore upper and lowercase
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }

  // 이름이 같을 경우
  return 0;
});
```
{% endtab %}
{% endtabs %}

## indexOf

### Description

`indexOf` 메서드는 배열에서 지정된 요소를 찾을 수있는 첫 번째 인덱스를 반환하고 존재하지 않으면 `-1`을 반환합니다.

### Syntax

```javascript
arrayObj.indexOf(element)
```

#### Parameter

* arrayObj
  * 배열 객체
* element
  * 찾을 요소

### Example

{% tabs %}
{% tab title="Case 1" %}
```javascript
var a = [2, 9, 9]; 
a.indexOf(2); // 0 
a.indexOf(7); // -1

if (a.indexOf(7) === -1) {
  // 요소가 배열에 존재하지 않습니다.
}
```
{% endtab %}
{% endtabs %}

### Polyfill

* IE 8 이하 지원 안함 

```javascript
var indexOf = Array.prototype.indexOf || (function (prop, s) {
  for (var i = (s || 0); i < this.length; i++) {
    if (this[i] === prop) { return i; };
  }

  return -1;
});
```

