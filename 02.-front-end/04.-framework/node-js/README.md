# Node JS

## HTTP 트랜잭션

#### 서버 생성 
모든 `node` 웹 서버 어플리케이션은 웹 서버 객체를 만들어야 합니다.  
이때 `createServer` 를 이용합니다.

```javascript
const http = require('http');
const server = http.createServer((req, res) => {
  // Work Process
});
```

서버로 오는 모든 HTTP 요청 마다 `createServer` 에 전달된 함수가 한번씩 호출된다.  
`createServer` 가 반환한 `Server` 객체는 `EventEmitter` 이고 `server` 객체를 생성하고 리스너를 추가하는 축약 문법이다.

> `EventEmitter` 이란 ?  
> 이벤트 모듈의 의해 정의 되며 새로운 이벤트가 추가되거나 삭제될 때 이벤트를 내보냅니다.

```javascript
const http = require('http');
const server = http.createServer();
server.on('request', (req, res) => {
  // Work Process
});
```

HTTP 요청이 서버에 오면 `node` 가 트랜잭션을 다루려고 `request` 와 `response` 객체를 전달하며 요청 핸들러 함수를 호출 합니다.

#### Method, URL, Header 의 처리

요청을 처리할 때, 우선은 Method 와 URL 을 확인한 후 이와 관련된 작업을 실행합니다.  
`node` 는 `request` 객체에 대부분의 프로퍼티를 넣어두므로 꺼내서 사용하면 된다.

```javascript
const {method, url} = request;
```

`request` 객체는 IncomingMessage 의 인스턴스이다.  

> `IncomingMessage Class` 의 특징
> * HTTP 에 의해 생성된다.
> * 특정 객체의 첫번째 변수로 전달되는 인수 (`SERVER` `http.ClientRequest` `request event` `response event`)
> * 응답상태 및 헤더, 데이터 등을 액세스 하는데 사용 한다.

헤더 또한 `request` 객체에서 얻어온다.

```javascript
const {headers} = request;
const userAgent  = header['user-agent'];
```

> Tips
>
> 클라이언트가 설정한 헤더 프로퍼티는 대소문자 구분없이 _**소문자로만 표현**_ 된다.  
> 일부 헤더 정보를 반복해서 설정하면 overwrite 하거나 csv 형태로 구성될 수 있다. 이런 경우에는 `rawHeaders` 를 사용할 수 있다.

#### Request Body 의 처리

`post` 혹은 `put` 요청시 핸들러에 전달된 `request` 객체는 `ReadableStream` 인터페이스를 구현하고 있다.  
이 스트림에 `EventListener` 를 등록하거나 다른 스트림의 파이프로 연결 할 수 있다.

각 `data` 이벤트에서 발생시킨 청크는 `Buffer` 이며 이는 문자열 데이터이다.  
이는 `end` 이벤트에서 이어 붙인 다음에 문자열로 만드는게 가장 좋다.

```javascript
let body = [];

request.on('data', (chunk) => {
  body.push(chunk);
}).on('end', () => {
  // `body` 에 전체 요청 바디가 문자열로 담겨 있다.
  body = Buffer.concat(body).toString();
});
```












> Reference URL 
> 
> https://nodejs.org/ko/docs/guides/anatomy-of-an-http-transaction/