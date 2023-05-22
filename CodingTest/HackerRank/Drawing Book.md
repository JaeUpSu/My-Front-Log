<img src="../../Image/hackerrank.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# 🔩 `Drawing Book Problem`

<br>


* **문제**
* **풀이**
* **코드**

<br>

> 문제
```
주어진 매개변수로 
n : 마지막 페이지 수
p : 사용자가 원하는 페이지 수

앞에서부터 원하는 페이지로 넘기거나 
뒤에서부터 원하는 페이지까지 넘겼을 때 
더 적은 횟수로 넘기는 방법을 찾기
```

<br>
<br>

> 풀이

<br>

- 책은 왼쪽, 오른쪽 두 페이지가 존재

    - 주어진 페이지 번호 / 2 를 해주면 해당 페이지가 몇 번째 장인지 알 수 있다.

<br>
<br>

> 코드

```typescript
function pageCount(n: number, p: number): number {

    const frontFlip = Math.floor(p/2);
    const backFlip = Math.floor((n/2)-frontFlip);
    const result = Math.min(frontFlip, backFlip);

    return result;
}
```