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

## React Development Tools

손쉬운 디버그 환경을 위하여 _**크롬 확장프로그램**_ \(Chrome Extension\) 에서 해당 플러그인을 설치한다.

![React Development Tools](/img/A004.png)

> ### 참고자료
> * React
>   * [https://d2.naver.com/helloworld/1848131](https://d2.naver.com/helloworld/1848131)
>   * [https://reactjs.org/docs/getting-started.html](https://reactjs.org/docs/getting-started.html)
>   * [https://velopert.com/3613](https://velopert.com/3613)
> * Redux
>   * [https://deminoth.github.io/redux/](https://deminoth.github.io/redux/)

## 왜 가상 돔 (Virtual DOM) 이 빠른이유

DOM 구조상의 Node 변경점이 생기면 레이아웃을 만들고 페인팅을 하는 과정에서 리소스가 발생된다.  
만약 30개의 노드가 바뀐다고 가정하면 30번의 (잠재적인) 레이아웃 재계산과 30번의 리랜더링을 초래하는것이다.  
이는 React 를 사용했을때 DOM 조작이 최종적인 결과물만 반영되기 때문에 모든 변화를 하나로만 묶어서 변화 시키는 것이다.  

즉 _**브라우저가 연산하는 횟수를 줄이는데 집중**_ 한다.

물론 최종 결과 값만 변경되기 때문에 궂이 Virtual DOM 을 사용하지 않아도 변화를 묶어서 DOM 에 반영 시켜 주면 되지만  
_**Virtual DOM 은 DOM fragment 를 관리하는 과정을 수동으로 하나하나 작업할 필요없이 자동화 하고 추상화하는것**_ 에 있다.  
이러한 부분들을 자동화 해주는 편의를 제공하기 때문에 충분히 매력적이고 강력한 뷰 라이브러리인 것이다.

각 컴포넌트가 DOM 조작을 요청할 때 다른 컴포넌트들과 상호작용하지 않아도 되며, 특정 DOM 을 조작할 것이라던지, 혹은 이미 조작했다던지에 대한 공유를 할 필요가 없다.

즉 각각의 변화들을 동기화 작업을 거치지 않으면서 하나의 작업으로 묶을수 있는것이다.

> ### 참고자료
> <https://velopert.com/3236>

## Class Constructor 에서 `super()`

컴포넌트 안에서 생성자 (constructor) 를 실행하면 반드시 `super()` 를 실행해야 한다.  
생성자 (constructor) 를 사용하지 않으면 자동으로 실행해준다.

이는 `this` 객체를 초기화 해주지 않기 때문이다.

```es6
class Myclass extends React.Component {
  constructor() {
    console.log(this);   // Error : 'this' is not allowed before
    super();
  }
}
```

위와 같이 `super()` 실해 이전에 `this` 를 참조하면 허용되지 않는다.

`super()` 를 호출할때 `props` 인자를 넘겨주면 constructor 안에서 `this.props` 를 접근 가능하게 구성해준다.

```es6
class Myclass extends React.Component {
  constructor(props) {
    super(props);
  }
}
```

위와 같이 사용해야 정상적으로 `this.props` 사용이 가능하다.


> ### 참고자료
> <https://medium.com/@umioh1109/react-es6-class-constructor%EC%97%90%EC%84%9C%EC%9D%98-super-9d53ba0611d9>