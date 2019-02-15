# 삽입 \(Insertion\)

전체요소에서 가장 작은 데이터를 찾아 가장 앞의 데이터와 교환하는 방식

```javascript

const array = [5, 3, 1, 4, 2];

let len = array.length, i = 1, j, temp;

for (; i < len; ++i) {
  temp = array[i];
  j = i;

  while (j > 0 && array[j - 1] > temp) {
    array[j] = array[j - 1];

    j--;
    cnt++;
  }

  array[j] = temp;
}

console.log(array.join(' '));
```