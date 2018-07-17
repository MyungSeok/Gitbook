# Node JS

## Express

### Route

라우팅은 요청 URI 및 특정한 HTTP 요청 메소드 \(GET, POST, PUT, DELETE\) 인 특정 _**엔드포인트**_ 에 대한 클라이언트 요청에 대해 애플리케이션이 응답하는 방법을 결정 하는것 

```javascript
app.METHOD(PATH, HANDLER)
```

#### Parameter

* app
  * `express` 의 인스턴스 
* METHOD
  * HTTP 요청 메소드
* PATH
  * 서버 경로
* HANDLER
  * 라우트가 일치할 때 실행되는 함수

#### Example

각 요청에 따른 라우트를 정의하고 이에 응답한다.

```javascript
var express = require('express');
var app = express();

app.get('/', function(req, res) {
  res.send('hello world');
});
```

대표적인 Express 라우팅 메소드는 다음과 같다.

{% tabs %}
{% tab title="GET" %}
```javascript
app.get('/', function (req, res) {
  res.send('Hello World!');
});
```
{% endtab %}

{% tab title="POST" %}
```javascript
app.post('/', function (req, res) {
  res.send('Got a POST request');
});
```
{% endtab %}

{% tab title="PUT" %}
```javascript
app.put('/user', function (req, res) {
  res.send('Got a PUT request at /user');
});
```
{% endtab %}

{% tab title="DELETE" %}
```javascript
app.delete('/user', function (req, res) {
  res.send('Got a DELETE request at /user');
});
```
{% endtab %}
{% endtabs %}

라우팅 경로는 문자열 기반의 패턴도 대응한다.

{% tabs %}
{% tab title="Case 1" %}
```javascript
// acd, abcd
app.get('/ab?cd', function(req, res) {
  res.send('ab?cd');
});
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
// abcd, abbcd, abbbcd
app.get('/ab+cd', function(req, res) {
  res.send('ab+cd');
});
```
{% endtab %}

{% tab title="Case 3" %}
```javascript
// abcd, abxcd, abRABDOMcd, ab123cd
app.get('/ab*cd', function(req, res) {
  res.send('ab*cd');
});
```
{% endtab %}

{% tab title="Case 4" %}
```javascript
// /abe, /abcde
app.get('/ab(cd)?e', function(req, res) {
 res.send('ab(cd)?e');
});
```
{% endtab %}
{% endtabs %}

정규식 패턴 대응 

{% tabs %}
{% tab title="Case 1" %}
```javascript
// a 가 포함된 모든 항목과 일치 
app.get(/a/, function(req, res) {
  res.send('/a/');
});
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
// butterfly, dragonfly 과는 일치 
// butterflyman, dragonfly man 과는 불일치 
app.get(/.*fly$/, function(req, res) {
  res.send('/.*fly$/');
});
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Express 는 HTTP 메소드에 해당하는 다음과 같은 라우팅 메소드를 지원한다.

`get`, `post`, `put`, `head`, `delete`, `options`, `trace`, `copy`, `lock`, `mkcol`, `move`, `purge`, `propfind`, `proppatch`, `unlock`, `report`, `mkactivity`, `checkout`, `merge`, `m-search`, `notify`, `subscribe`, `unsubscribe`, `patch`, `search`및 `connect`.
{% endhint %}

#### 



