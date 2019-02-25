# 트리 (Tree)

자료구조상의 _**트리**_ 는 다음과 같은 특성을 가진다.

* 트리는 하나의 루트 노드를 가진다.
* 트리는 0개 이상의 자식 노드를 갖고 있다.
* 그 자식노드 또한 0개 이상의 자식 노드를 갖고 있으며, 이를 반복적으로 정의한다.

트리는 비 순환 그래프의 한 종류 이다.

## 트리의 종류

### 포화 이진 트리 (Full Binary Tree)

![포화 이진 트리](/img/A036.png)

트리의 모든 노드의 깊이가 같은 완전한 이진 트리를 말한다.

### 완전 이진 트리 (Complete Binary Tree)

![완전 이진 트리](/img/A037.png)

노드의 마지막 부분 (끝 부분) 을 제외하고는 모든 자식 노드를 2개를 가진 이진 트리를 말한다.

### 이진 트리 (Binary Tree)

트리중에서도 각 노드의 _**자식노드가 최대 2개**_ 를 갖고 있는 트리를 말한다.

## 트리의 순회 (탐색)

트리의 순회 방식은 대표적으로 다음 3가지로 나뉜다.

* 전위 순회 (Pre-order traversal)
* 중위 순회 (In-order traversal)
* 후위 순회 (Post-order traversal)

> ### 참고자료
> <https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html>
> <https://secmem.tistory.com/204>