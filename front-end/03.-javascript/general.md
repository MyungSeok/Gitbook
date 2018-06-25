# General

## JSONP

웹 브라우저는 _**SOP \(same origin policy: 동일출처정책\)**_ 에 따라 서로 다른 도메인간의 데이터 통신을 제한하고 있다   
script 코드가 _**DOM 트리에 추가되어 실행되면 외부 스크립트를 로드할 수 있다는 것**_에서 착안   
`<script>` 태그는 SOP 정책에 속하지 않기 때문에 jsonp \(json width padding\) 이 사용됨

![Ajax&#xC640; jsonp&#xC758; &#xBE44;&#xAD50;](../../.gitbook/assets/undefined.tiff)

{% hint style="warning" %}
JSONP 의 callback 은 _**서버에서 지원**_ 해줘야 정상적으로 사용이 가능
{% endhint %}



