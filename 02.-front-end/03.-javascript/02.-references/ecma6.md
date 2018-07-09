# ECMA6

## arrows

### Description

화살표 함수 표현식은 축약형 함수 입니다.

### Syntax

```javascript
(param1, param2, ... , paramN) => { statements }
```

#### Parameters 

* statements
  * 함수의 내용

### Example 

{% tabs %}
{% tab title="Case 1" %}
```javascript
// 매개변수가 하나 이상있는 경우는 괄호가 필요
(param1, param2) => {
    return param1 + param2
};

// 매개변수가 하나인 경우에는 괄호가 필요 없음
param1 => {
    return param1 + 1
}
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
가 하나 이상
```
{% endtab %}
{% endtabs %}

