<img src="../../Image/hackerrank.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# 🔩 `Zig Zag Sequence Problem`

<br>


* **문제**
* **풀이**
* **코드**

<br>

> 문제
```
주어진 n 길이의 input 값을 배열로 전환한다.

후에 (n + 1) / 2 기준으로 좌우로 내림차순, 오름차순으로 정렬해서 합친 배열 구하기
```

<br>
<br>

> 풀이

<br>

- split("\n") 을 통해 추출

    - 스프레드 연산자를 통해 문자열을 배열로 전환

<br>

- arr 에서 `k = (arr.length + 1) / 2` 기준으로 좌우로 배열 추출
    - 좌 : arr.slice(0, k)
    - 우 : arr.slice(k)

<br>

- 각 분리된 배열을 좌우로 다르게 정렬
    - 좌 : arr.slice(0, k).sort((a, b) => a - b);
    - 우 : arr.slice(k).sort((a, b) =>  b - a);

<br>

- 각 분리된 배열을 concat 으로 병합
    - 좌.concat(우)


<br>
<br>

> 코드

```typescript
function processData(input) {
  //Enter your code here
  let builtArray = [];
  for (let i = 4; i < input.length; i++) {
    if (input[i] !== ' ') {
      builtArray.push(+input[i]);
    }
  }
  
  let firstHalf = builtArray.slice(0, (builtArray.length / 2)).sort((a, b) => a - b);
  let secondHalf = builtArray.slice((builtArray.length / 2)).sort((a, b) => b - a);
  
  let zigzagArray = firstHalf.concat(secondHalf);
  
  console.log(...zigzagArray);
}
```