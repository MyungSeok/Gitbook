# Promise

JavaScript 특성상 싱글 스레드 환경에서 대부분의 작업들은 비동기로 이루어진다.

하지만 최근에 자바스크립트 기술의 발전과 하나의 작업을 콜백으로 결과를 받은뒤 순차적으로 작업을 수행하고자 한다면 아래와 같은 콜백 중첩 (콜백 지옥) 을 경험하게 된다.

```javascript
async(1, function () {
  async(2, function () {
    async(3, function () {
      async(4, function () {
        async(5, function () {
          console.log('작업 완료???!!??!!')
        });
      });
    });
  });
});
```

이러한 상황을 극복하기 위해 오래전부터 Promies 라는 패턴이 제안되어 왔으며 다양한 라이브러리를 통해서 이를 구현하여 사용해 왔다.

`Promise` 패턴은 ES5 환경에서 일부 브라우저에서 사용 가능하며 ES6 에 정식 스팩에 포함되었다. 

> IE 는 사용 불가하여 Polyfill 코드를 사용하여 구현해야 함  
> Chrome, FF 는 Full Support

## Syntax

```javascript
new Promise(function (resolve, reject) {
  /* statement */
});
```

실행시 `Promise` 구문에서 실행한 익명함수의 반환값은 무시된다.

### Parameter

* resolve
  * 성공시 전달되는 인수 (함수 혹은 변수)
* reject
  * 실패시 전달되는 인수 (함수 혹은 변수)

## Example 1 

```javascript
var _promise = function (param) {
  return new Promise(function (resolve, reject) {
    window.setTimeout(function () {
      if (param) {
        resolve('Success');
      } else {
        reject(Error('Failed'));
      }
    });
  });
}

_promise(true)
  .then(function (message) {
    console.log(message);
  }, function (error) {
    console.error(error);
  });
```

`Promise` 사용시 다음 상태중에 하나가 될 것이다.

* pending
  * 아직 `Promise` 를 수행중인 상태 
* fulfilled
  * `Promise` 가 성공적인 상태이다.
* rejected
  * `Promise` 가 실패한 상태이다.
* settled
  * `Promise` 성공여부와 상관없이 완료된 상태이다.

# 작성중

> Reference
> 
> <https://programmingsummaries.tistory.com/325>
> <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise>