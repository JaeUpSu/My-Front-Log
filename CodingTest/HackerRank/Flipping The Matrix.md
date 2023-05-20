<img src="../../Image/hackerrank.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# 🔩 `Flipping The Matrix`

<br>


* **문제**
* **문제 예시**
* **풀이**
* **코드**

<br>

> 문제

```
주어진 2n x 2n 배열에서 각 요소의 위치를 바꿔 
upper left quadrant 인 n x n 의 크기의 요소의 합이 가장 큰 값을 반환
```

<br>
<br>

> 문제 예시

```javascript
112  42  83 119
 56 125  56  49
 15  78 101  43
 62  98 114 108
 
112  42 114 119
 56 125 101  49
 15  78  56  43
 62  98  83 108
 
"119 114"  42 112   
" 56 125" 101  49
 15  78    56  43
 62  98    83 108
```
---
```
합 : 119 + 114 + 56 + 125
```


<br>
<br>

> 풀이

<br>

- 매트릭스 가장 좌측상단의 1열1행에 있는 값은 아무리 회전한들 결국 존재할 수 있는 위치가 정해져 있다.

    - n열 n행 , 1열 n행 , n열 1행 , 1열 1행 
    - 이렇게 4 군데만 위치 가능

<br>

- 해당 4 군데의 위치 값중 가장 큰 값이 1열 1행에 존재

<br>

- 모든 매트릭스의 값들도 마찬가지로 적용

        - matrix[row][col]
        - matrix[row][2 * size - col - 1]
        - matrix[2 * size - row - 1][col]
        - matrix[2 * size - row - 1][2 * size - col - 1]

<br>

- 이 4 군데의 값중 가장 큰 값이 좌측 상단에 오게되고 해당 값들을 더하기

<br>
<br>


-  | |0|1|2|3|
   |---|---|---|---|---|
   |0|**`a`**|**`b`**|b|a|
   |1|**`c`**|**`d`**|d|c|
   |2|c|d|d|c|
   |3|a|b|b|a|

<br>
<br>

> 코드

```typescript
const flippingMatrix = (matrix : number[][]) : number => {

let total = 0;
const size = matrix.length / 2;

for (let row = 0; row < size; row++) {
    for (let col = 0; col < size; col++) {
        max = Number.MIN_VALUE;
        max = Math.max(matrix[row][col], max);
        max = Math.max(matrix[row][2 * size - col - 1], max);
        max = Math.max(matrix[2 * size - row - 1][col], max);
        max = Math.max(matrix[2 * size - row - 1][2 * size - col - 1], max);

        total += max;
    }
}

return total;
}
```