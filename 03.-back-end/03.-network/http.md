# HTTP

## HTTP Header

### Request Header

클라이언트 브라우저에서 HTTP 프로토콜을 이용하여 _**요청 정보를 웹 서버로 전송할 때**_ HTTP 요청 헤더에 부가적인 정보를 담아 전송한다.

* Accept
  * 클라이언트가 처리하는 미디어 타입 
* Accept-encoding
  * 클라이언트가 해석할 수 있는 인코딩 방식
* Accept-language
  * 클라이언트가 지원하는 언어  
* Connection
  * 클라이언트와 서버의 연결 방식 
    * keep-alive : 클라이언트와 접속 유지 
    * close : 클라이언트와 접속 중단 
* Host
  * 호스트 이름 URI 와 PORT 번호 정보 
* User-agent
  * 클라이언트 브라우저 정보 

### Response Header 

서버가 HTTP 프로토콜을 이용하여 클라이언트의 요청에 대해 응답할 때 부가적인 정보를 응답 헤더에 담아 전송한다.

* Connection
  * 클라이언트와 서버의 연결 방식 설정 
    * keep-alive : 클라이언트와 접속 유지 
    * close : 클라이언트와 접속 중단 
* Content-Length
  * 요청한 파일의 데이터 길이 
* Content-Type
  * 헤더 응답 문서의 mime 타입
* Date
  * 현재 일시를 GMT 형식으로 지정
* Server
  * 웹 서버 정보 

## Timeout

### Connection Timeout

Connection 을 구성하는데 소요되는 시간

### Read Timeout

Server 에서 데이터를 완전히 받을때 까지 걸리는 시간

## MIME

서버가 클라이언트에게 전송되는 문서에 대한 유형을 지칭하는 타입

### Syntax

```markup
[파일의종류]/[파일타입]
```

### Type List

* text
  * 텍스트 파일 
  * text/plain, text/html, text/css, text/javascript
* multipart
  * 이미지 파일 \(비디오 제외\)
  * audio/midi, audio/mpeg, audio/webm, audio/ogg, audio/wav
* audio
  * 오디오 파일
  * audio/midi, audio/mpeg, audio/webm, audio/ogg, audio/wav
* video
  * 비디오 파일
  * video/webm, video/ogg
* application
  * 모든 바이너리 타입
  * application/octet-stream, application/pkcs12, application/vnd.mspowerpoint, application/xhtml+xml, application/xml,  application/pdf

