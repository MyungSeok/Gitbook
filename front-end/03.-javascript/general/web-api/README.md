# Web API

## XMLHttpRequest

서버와의 비동기 데이터 통신을 하기 위해서 `XMLHttpRequest` 객체를 할 수 있다.  
기존의 자바스크립트의 `ajax` 을 사용하는 것과 동일하다.

### \#1 HTTP Request 생성 

모든 브라우저에서 사용 가능한 인스턴스를 생성한다.

```javascript
var xhr
if (window.XMLHttpRequest) {
    xhr = new XMLHttpRequest();
} else if (window.ActiveXObject) {
    xhr = new ActiveXObject('Microsoft.XMLHTTP');
}
```

### \#2 응답 데이터를 처리할 `callback` 함수를 정의

```javascript
var successCallback = function () {
    // 서버에서 받은 응답을 프로세
}

xhr.onreadystatechange = successCallback;
```

### \#3 요청 \(Request\) 와 응답 \(Response\) 을 정의

