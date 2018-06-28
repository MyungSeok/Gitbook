---
description: Function 생성자 객체에 대해 정의합니다.
---

# Function

## bind

### Description

`bind()` 메소드는 호출될 때 그 `this` 키워드를 제공한 값으로 설정하고 새로운 함수를 생성합니다.  
_**실행하지 않고 함수만 반환**_ 한다.

### Syntax

```javascript
func.bind(thisArg[, arg1[, arg2[, ... ]]];
```

#### Parameters

* thisArg
  * 바인딩된 함수가 호출될 때 대상함수에 `this` 매개변수로서 전달되는 값 
* arg1, arg2, ...
  *  대상 함수를 호출할 때 바인딩된 함수에 제공되는 인수

#### Retrun Value

* 지정된 `this` 값 및 초기 인수가 있는 주어진 함수의 복제본 

## call

### Description

`call()` 메소드는 호출될 때 제공된 `this` 키워드 값과 인수를 함께 호출합니다.

### Syntax

```javascript
func.call(thisArg[, arg1[, arg2[, ... ]]];
```

#### Parameters

* thisArg
  * 바인딩된 함수가 호출될 때 대상함수에 `this` 매개변수로서 전달되는 값 
* arg1, arg2, ...
  *  대상 함수를 호출할 때 바인딩된 함수에 제공되는 인수

## apply

### Description

`apply()` 메소드는 호출될 때 제공된 `this` 키워드 값과 인수를 함께 호출합니다.

### Syntax

```javascript
func.call(thisArg, [argsArray];
```

#### Parameters

* thisArg
  * 바인딩된 함수가 호출될 때 대상함수에 `this` 매개변수로서 전달되는 값 
* argsArray
  *  대상 함수를 호출할 때 바인딩된 함수에 제공되는 인수의 배열

 

