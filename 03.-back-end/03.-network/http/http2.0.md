# HTTP 2.0

## HTTP1 의 요청 방식

HTTP1 에서는 앞에서 날렷던 요청의 응답을 받아야만 다음 요청이 처리될 수 있다.

```mermaid
  sequenceDiagram
    Note over Client, Server : Establish Connection
    Client ->> + Server : Request
    Note right of Server: Blocked
    Server ->> - Client : Response
    Note over Client, Server : Close Connection
    Note over Client, Server : Establish Connection
    Client ->> + Server : Request
    Note right of Server: Blocked
    Server ->> - Client : Response
    Note over Client, Server : Close Connection
```

이러한 현상을 해결 하기위해 지속 커넥션 (Persistent Connection) 이라는 개념과 HTTP 파이프 라이닝 (Pipelining) 이라는 개념이 들어갔다.  
커넥션을 재사용할 수 있고, `Request` 를 미리 여러개 서버로 요청할 수 있게 되었다.

하지만 근본적으로 `Request` 보낸 순서대로 `Response` 를 받을수 있다는 점에서는 문제해결이 어려워 보인다.

## HOL (Head-of-Line Blocking) 의 문제점

만약 처음에 요청한 `Request` 에 문제가 있어 `Response` 가 늦어지면 2번째, 3번째에 요청한 `Request` 의 `Response` 도 늦어지는 문제점이 발생한다.

```mermaid
  gantt
    title Head-Of-Line Blocking
    dateFormat  YYYY-MM-DD
    section HTTP
    Request 1     : crit, 2000-01-01  , 12d
    Request 2     : 6d
    Request 3     : 6d
```

## 도메인 샤딩

_**HOL**_ 과 같은 문제들을 해결하기 위하여 리소스를 도메인 별로 분리해서 자원을 받는 방법  
도메인별로 리소스를 병렬적으로 동시에 받을수 있다.

```mermaid
  gantt
    title Domain Sharding
    dateFormat  YYYY-MM-DD
    section www.example.com
    index.html     : html, 2000-01-01  , 8d
    section A.example.com
    style_1.css     : after html, 6d
    style_2.css     : after html, 6d
    section B.example.com
    resource_1.js     : after html, 6d
    resource_2.js     : after html, 6d
```

하지만 하나의 도메인별 브라우저에서 받을수 있는 스팩의 제한 이나 _**DNS Lookup 과정과 TCP Handshake 과정에서 소요되는 시간**_ 때문에 오히려 부작용 발생 가능성이 있다.

> 브라우저당 도메인별 리소스 다운 제한은 보통 _**6 ~ 8 개정도**_ 이며 `iframe` 은 제외이다.

## 그 외 방법들

_**HTTP 1.1**_ 에서는 다음과 같은 방법을 통해서도 성능개선을 시도하였다.

1. HTTP 요청 최소화
    1. 큰 이미지를 틍으로 요청후 CSS 로 잘게 잘라서 사용
    2. BASE64 인코딩된 이미지를 요청해서 사용
2. 소스 압축
    1. HTML 의 gzip 압축 전송
    2. JS, CSS 의 소스 압축

## HTTP 2.0 의 다른점

### 바이너리로 인코딩된 데이터 전송

바이너리 포맷의 데이터를 사용하게 되어 하나의 플레인 데이터를 프레임 단위로 나눠서 관리 및 전송할 수 있다.

HTTP 2.0 은 Frame 과 Stream 이라는 개념이 적용 되었다.

> HTTP 1.x 시절에는 요청 (Request) 과 응답 (Response) 으로 명확히 구분되었다.

* Frame
  * HTTP2 통신에서 데이터를 주고 받을수 있는 가장 작은 단위의 데이터
  * 헤더 프레임, 데이터 프레임으로 구성
* Stream
  * `Server` 와 `Client` 사이의 양방향으로 데이터를 주고 받는 한개 이상의 _**메세지**_ 를 의미한다.

> 스트림 = 메세지 + ... + 메세지  
> 메세지 = 프레임 + ... + 프레임

### Server Push

요청한 클라이언트에게 서버가 알아서 필요한 리소스를 찾아서 내려준다.

하지만 _**브라우저가 캐싱된 데이터**_ 나 _**필요없는 리소스 데이터**_ 는 자원의 낭비를 초래할 수 있다.

### 헤더의 압축

HTTP2 의 Header 는 _**Header Table 로 관리**_ 되어 _**이전 요청에서 중복으로 선언된 헤더는 인덱스 값만 전송하여 데이터를 최소화**_ 한다.

### 적용 방법

1. TSL / SSH 인증서 필요
2. 웹서버의 세팅