# Vue

## 템플릿 연동

```javascript
  export default {
    beforeCreate() {
      /* 가장 먼저 실행되는 훅으로 event 가 세팅되지 않는 시점 */
    },
    created() {
      /* `data` 와 `event` 가 활성화 되어 접근 가능한 상태 */
    },
    beforeMount() {

    },
    data() {
      value = null
    },
    methods: {
      /* 내부 함수목적으로 주로 사용 */
    },
    /* 계산된 속성은 원래 getter 목적으로만 사용 */
    /* 필요에 의해서 setter 사용 가능 */
    computed: {
      getValue: {
        get: function () {
          return this.value;
        },
        set: function (value) {
          this.value = value;
        }
      }
    },
    /* 변수가 변경되는 것을 감지 */
    watch: {
      getValue(newValue, oldValue) {
        console.log('새로운 값 : ' + newValue);
        console.log('오래된 값 : ' + oldValue);
      }
    }
  }
```

## 동기

```javascript
store.commit('syncFunc');
```

```javascript
new Vuex.Store({
  state: {},
  mutations: {
    // 반드시 함수형이여야 한다.
    syncFunc: (state) => {
      /* statement */
    }
  }
});
```

## 비동기

```javascript
store.dispatch('asyncFunc');
```

```javascript
new Vuex.Store({
  state: {},
  actions: {
    // 반드시 함수형이여야 하며 클로져나 스코프체인의 보장이 어렵다.
    asyncFunc: (state) => {
      /* statement */
    }
  }
});
```
