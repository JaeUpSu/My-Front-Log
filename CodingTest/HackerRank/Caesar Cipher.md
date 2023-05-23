<img src="../../Image/hackerrank.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# 🔩 `Caesar Cipher Problem`

<br>


* **문제**
* **풀이**
* **코드**

<br>

> 문제
```
s : 암호화할 문자열
k : k 만큼 계산하여 변환

s 를 k 만큼 계산해서 암호화한 문자열 반환하기
소문자, 대문자 따로 처리
```

<br>
<br>

> 풀이

<br>

- 소문자 "a,b,c,...,z"
    - 대문자 "a,b,c,...,z".toUpperCase()      

<br>

- s.split("") 으로 Array 반환하여 map 으로 암호화 처리
    - 소문자 Idx 구하고 k 만큼 더하고 알파벳 개수만큼 
      나눈 나머지 idx 알파벳 반환
    - 대문자 Idx 구하고 k 만큼 더하고 알파벳 개수만큼 
      나눈 나머지 idx 알파벳 반환
    - 알파벳을 제외한 나머지 문자는 그대로 반환

<br>

- res.join("") 으로 배열을 문자열로 반환

<br>
<br>

> 코드

```typescript
function caesarCipher(s: string, k: number): string {
    // Write your code here
    const lowerA = "abcdefghijklmnopqrstuvwxyz"
    const upperA = lowerA.toUpperCase()

    const res = s.split("").map(c => {
    if (lowerA.includes(c)) {
        return lowerA[(lowerA.indexOf(c) + k) % 26]
    } else if (upperA.includes(c)) {
        return upperA[(upperA.indexOf(c) + k) % 26]
    } else {
        return c
    }
    })

    return res.join("")
}
```