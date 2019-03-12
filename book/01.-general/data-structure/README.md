# Data Structure

자료를 효율적으로 이용할 수 있도록 컴퓨터에 저장하는 방법이다.

```mermaid
  graph LR
    A["자료형"] --> B["단순 구조"]
    B --> F["정수"]
    B --> G["실수"]
    B --> H["문자"]
    B --> I["문자열"]
    A["자료형"] --> C["선형 구조"]
    C --> J["순차 리스트"]
    C --> K["연결 리스트"]
    J --> O["단순 연결 리스트"]
    J --> P["이중 연결 리스트"]
    J --> Q["원형 연결 리스트"]
    C --> L["스택"]
    C --> M["큐"]
    C --> N["덱"]
    A["자료형"] --> D["비선형 구조"]
    D --> R["트리"]
    R --> T["일반 트리"]
    R --> U["이진 트리"]
    D --> S["그래프"]
    S --> V["방향 그래프"]
    S --> W["무방향 그래프"]
    A["자료형"] --> E["파일 구조"]
    E --> X["순차 파일"]
    E --> Y["색인 파일"]
    E --> Z["직접 파일"]
```

## List 와 Map 의 비교

### List

* 순차적으로 데이터를 저장한다.
* 값의 중복이 허용된다.
* 순차적인 접근이 필요할 경우 사용

### Map

* 키를 중복으로 저장불가 하다. (값은 가능)
* 빈 공간을 찾아서 저장하기 때문에 List 보다는 데이터 저장속도가 느릴수 있다.
* 키값을 통해서 빠르게 데이터 검색 가능