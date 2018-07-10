# React JS

## ESLint

`.eslintrc.json` 파일에 다음과 같이 추가해준다.  
es6 문법과 jsx 를 혼용하기 때문에 아래와 같은 lint 설정을 추가해준다.

```javascript
{
    ...
    "parserOptions": {
        "ecmaVersion": 6,
        "sourceType": "module",
        "ecmaFeatures": {
            "jsx": true
        }
    }
    ...
}
```

{% hint style="info" %}
참고 자료 

* React 
  * [https://d2.naver.com/helloworld/1848131](https://d2.naver.com/helloworld/1848131) 
  * [https://reactjs.org/docs/getting-started.html](https://reactjs.org/docs/getting-started.html) 
  * [https://velopert.com/3613](https://velopert.com/3613)
* Redux
  * [https://deminoth.github.io/redux/](https://deminoth.github.io/redux/)
{% endhint %}



