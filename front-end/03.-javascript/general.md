# General

## JSONP

웹 브라우저는 _**SOP \(same origin policy: 동일출처정책\)**_ 에 따라 서로 다른 도메인간의 데이터 통신을 제한하고 있다   
script 코드가 _**DOM 트리에 추가되어 실행되면 외부 스크립트를 로드할 수 있다는 것**_에서 착안   
`<script>` 태그는 SOP 정책에 속하지 않기 때문에 jsonp \(json width padding\) 이 사용됨

![Ajax&#xC640; jsonp&#xC758; &#xBE44;&#xAD50;](../../.gitbook/assets/undefined.tiff)

{% hint style="warning" %}
JSONP 의 callback 은 _**서버에서 지원**_ 해줘야 정상적으로 사용이 가능
{% endhint %}

{% tabs %}
{% tab title="Case 1" %}
#### 요청 URL 뒤에 callback 파라메터 추가하여 jsonp 요청 구현하기

#### Client

```javascript
$.getJSON('/jsonp.json?callback=?', function (data) {
    console.log('success: ', data);
});
```

#### Server

```java
private void doGet(HttpServletRequest request, HttpServleteResponse response) throws ServletException, IOException { 
    request.setCharacterEncoding("UTF-8");
    response.setCharacterEncoding("UTF-8");
          
    String id = request.getParameter("id");
    String callBack = request.getParameter("callback");
  
    JSONObject obj = new JSONObject();
    obj.put("result", id);
    obj.put("go", "테스트");
          
    PrintWriter out = response.getWriter();
    out.write(callBack + "(" + obj.toString() + ")");
    System.out.println(callBack + "(" + obj.toString() + ")");
    out.flush();
    out.close();
}
```
{% endtab %}

{% tab title="Case 2" %}
#### 요청 json 에 callback 함수로 한번 감싸서 jsonp 구현하

#### Client

```javascript
$.ajax({
  url: "/jsonp.json",
  dataType: 'jsonp',
  jsonpCallback: "myCallback",
  success: function(data) {
    console.log('성공 - ', data);
  },
  error: function(xhr) {
    console.log('실패 - ', xhr);
  }
});
```

#### Server

```java
myCallback({"message":"You got an AJAX response via JSONP from another site!"});
```
{% endtab %}

{% tab title="Case 3" %}
#### jsonpCallback 옵션 없이 사용하기

#### Client

```javascript
$.ajax({
  url: "/jsonp.json",
  dataType: 'jsonp',
  success: function(data) {
    console.log('성공 - ', data);
  },
  error: function(xhr) {
    console.log('실패 - ', xhr);
  }
});
```

#### Server

```java
jQuery18305806868467951786_1366340807385({"key":"value"});
```
{% endtab %}
{% endtabs %}

