# Web API

## SetTimeout

`WindowTimers` 에서 지원하는 타이머 객체로서   
_**자바스크립트 엔진이 일정시간 대기하였다가 UI 큐에 작업을 추가**_ 한다.

### Syntax

```javascript
[window.]setTimeout(callback[, delay[, param1[, ... paramN]]]);
```

#### Parameter

* window
  * `this` 객체가 window 일때 생략 가능 
* callback
  * 지연된 시간이 끝난 후 실행되는 콜백 함수 
* delay
  * 함수 지연 시간 \(default : 0\)
* param1 ... paramN
  * 콜백 함수로 전달될 매개변수 
  * IE9 이하에서는 매개변수 전달이 안된다. \(IE 10 이상 지\)

지정된 시간 이후에 UI 작업 큐에 추가되기 때문에 실제로 언제 실행 되는지는 알 수 없다.



