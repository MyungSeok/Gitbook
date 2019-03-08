# 스코프 (scope) 와 클로저 (closure)

## 렉시컬 스코프 (Lexical Scope)

스코프는 함수를 호출할 때가 아니라 _**선언할 때 생성**_ 된다.  
이것은 렉시컬 스코프의 특징이며 동적 스코프와 비교된다.

아래 예시에서는 선언할 때 생성되는 것을 확인할 수 있다.

```javascript
var color = 'red';

function foo() {
  var color = 'blue';
  function bar() {
    console.log(color);
  }
  return bar;
}

var baz = foo();
baz();
```

```javascript
blue
```

* ES5는 함수레벨의 렉시컬 스코프를 가진다.
* ES6는 함수레벨과 블록레벨의 렉시컬 스코프를 가진다.

## 동적 스코프 (Dynamic Scope)

함수가 어디서 호출되었는지에 따라 상위 스코프가 결정

```javascript
function foo() {
  console.log(x);
}

function bar() {
  var x = 15;
  foo();
}

var x = 10;
foo();
bar();
```

### 기존 (렉시컬 스코프)

```javascript
10
10
```

### 동적 스코프 가정 시

```javascript
10
15
```

> ### 참고자료
> <https://bestalign.github.io/2015/07/12/Lexical-Scope-and-Dynamic-Scope/>

## 순환참조

이는 잘못된 클로저 사용시 _**서로가 서로를 참조하는 순환 참조 현상이 발생**_ 될 수 있다.

순환참조가 발생되면 GC (Gabege Collection) 대상에서 벗어나기 때문에 메모리 누수의 원인으로 잔여하게 된다.

> ### 참고자료
> <https://hyunseob.github.io/2016/08/30/javascript-closure/>  
> <https://meetup.toast.com/posts/86>  
> <https://engineering.huiseoul.com/자바스크립트는-어떻게-작동하는가-메모리-관리-4가지-흔한-메모리-누수-대처법-5b0d217d788d>  
> <http://www.nextree.co.kr/p7363/>