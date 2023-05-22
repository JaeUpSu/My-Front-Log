<img src="../../Image/hackerrank.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# 🔩 `Tower Breaker Problem`

<br>


* **문제**
* **풀이**
* **코드**

<br>

> 문제
```
n : 타워의 수
m : 타워의 높이

타워의 수가 짝수 or 높이가 1일 경우
     => Player 2 Win !!!

나머지
     => Player 1 Win !!!
```

<br>
<br>

> 풀이

<br>

- 2 로 나눠지거나 타워의 높이가 1 인 경우만 player 2 승리

    - 삼항연산자 => n % 2 === 0 || m === 1 ? 2 : 1;


<br>
<br>

> 코드

```typescript
function towerBreakers(n : number, m : number) : number {
    return n % 2 === 0 || m === 1 ? 2 : 1;
}
```