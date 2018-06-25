---
description: 자바스크립트의 배열 객체
---

# Array

## Slice

배열의 일정 부분을 반환 합니다.

```javascript
arrayObj.slice(start, [end])
```

* arrayObj
  * **Array** 객체 
* start
  * arrayObject 에 대한 지정된 부분의 시작
* end
  * arrayObject 에 대한 지정된 부분의 끝

{% tabs %}
{% tab title="Example 1" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(1)
// ['e', 'l', 'l', 'o']
```
{% endtab %}

{% tab title=" Example 2" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(1, 4)
// ['e', 'l', 'l']
```
{% endtab %}

{% tab title="Example 3" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(0, -1)
// ['H', 'e', 'l', 'l']
```
{% endtab %}

{% tab title="Example 4" %}
```javascript
['H', 'e', 'l', 'l', 'o'].slice(-1, 0)
// []
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
이 메소드는 배열의 길이를 변하게 합니다.
{% endhint %}

## Shift

배열의 첫번째 요소를 제거하고, 제거된 요소를 반환합니다.

```javascript
arrayObj.shift()
```

{% tabs %}
{% tab title="Example 1" %}
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

## Map

`map()` 메소드는 배열내의 모든 요소에 대하여 제공된 함수\(callback\)를 호출하고, 그 결과를 모아서 _**새로운 배열을 반환**_ 합니다.

```javascript
var newAry = arrayObj.map(function callback(currentValue[, index[, array]]) {
    // newAry 의 새 요소를 반환
}[, thisArg]);
```

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

{% tabs %}
{% tab title="Example 1" %}
```javascript
var numbers = [1, 4, 9];
var roots = numbers.map(Math.sqrt);

console.log(numbers);
// [1, 4, 9]

console.log(roots);
// [1, 2, 3]
```
{% endtab %}

{% tab title="Example 2" %}
```javascript
var numbers = [1, 4, 9];
var doubles = numbers.map(function (num) {
    return num * 2;
});

console.log(doubles);
// [2, 8, 18]
```
{% endtab %}

{% tab title="Example 3" %}
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

## Filter

`filter()` 메소드는 배열내의 모든 요소에 대하여 제공된 테스트 함수\(callback\)를 호출하고, 그 결과를 모아서 _**새로운 배열을 반환**_ 합니다.

```javascript
var newAry = arrayObj.filter(function callback(currentValue[, index[, array]]) {
    // 반환형이 boolean 값 true 이면 값이 유지, false 이면 값 삭제
}[, thisArg]);
```

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

{% tabs %}
{% tab title="Example 1" %}
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
이 메소드는 배열의 요소를 변하게 합니다.
{% endhint %}

## ForEach

`forEach()` 메소드는 배열 요소마다 한 번씩 제공된 함수\(callback\) 함수를 호출해서 사용합니다.

```javascript
arrayObj.forEach(function callback(currentValue[, index[, array]]) {
    // 반환형 없이 각 요소마다 함수를 실행
}[, thisArg]);
```

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



