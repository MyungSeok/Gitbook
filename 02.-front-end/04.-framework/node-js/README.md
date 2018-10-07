# Node JS

## HTTP 트랜잭션

#### 서버 생성 

모든 `node` 웹 서버 어플리케이션은 웹 서버 객체를 만들어야 합니다.  
이때 `createServer` 를 이용합니다.

```javascript
const http = require('http');
const server = http.createServer((request, response) => {
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

#### 오류의 관한 처리

`request` 스트림에서 오류가 발생하면 `error` 이벤트가 발행하면서 오류를 전달한다.  
별도의 이벤트 리스너가 등록되어 있지 않다면 오류를 뱉으면서 Node.js 를 종료시킨다.

```javascript
request.on('error', (err) => {
  console.error(err.stack);
});
```

#### HTTP 요청 코드 정리
```javascript
const http = require('http');

http.createServer((request, response) => {
  const {headers, method, url} = request;
  
  let body = [];

  request.on('error', (err) => {
    console.error(err.stack);
  }).on('data', (chunk) => {
    body.push(chunk);
  }).on('end', () => {
    body = Buffer.concat(body).toString();

    /**
     *  헤더, 메서드, 요청경로, 바디 등을 가지게 되었으며 
     *  이 요청에 응답하는 작업을 수행할 수 있습니다.
     */
  })
}).listen(8080);
```

> 이 코드는 요청 받을 수 있지만 요청한 디바이스(클라이언트) 에 응답 하는 로직이 없기 때문에 타임아웃이 걸릴것 입니다.

#### 응답 상태 코드 

별도의 설정이 없으면 HTTP 응답 코드는 200 으로 고정 됩니다.  
상태 코드를 변경 하려면 `statusCode` 프로퍼티를 설정해야 합니다.

```javascript
// 리소스를 찾을수 없음 
response.statusCode = 404;
```

#### 응답 헤더 설정

setHeader 메서드로 헤더를 설정 한다.

```javascript
response.setHeader('Content-Type', 'application/json');
response.setHeader('X-Powered-By', 'bacon');
```

> 헤더 설정 프로퍼티의 대/소문자는 구분이 없다.

#### 명시적 헤더 데이터 전송

`writeHead` 메소드를 이용하여 명시적으로 헤더 작성이 가능하다.

```javascript
response.writeHead(200, {
  'Content-Type': 'application/json',
  'X-Powered-By': 'bacon'
});
```

> Reference URL 
> 
> https://nodejs.org/ko/docs/guides/anatomy-of-an-http-transaction/