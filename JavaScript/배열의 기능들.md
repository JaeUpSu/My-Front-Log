<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `배열의 내장 기능들을 알아보자`

<br>

* **정의**
* **기능**

<br>

> 정의

```
해당 메모들은 JavaScript 에서 
배열의 내장 기능 정리이다.
```
<br>

> 기능

<br>

- shfit & pop
- sort
- every
- slice

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`shfit & pop`

```
arr.shift() : 첫번째 값 삭제하면서 반환
arr.pop() : 마지막 값 삭제하면서 반환
```    

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`sort`

```
arr.sort() : 요소를 문자열로 변환하고 유니코드 코드 포인트를 기준으로 정렬

arr.sort((a,b) => a-b) : 올바른 숫자 기준 오름차순

arr.sort((a,b) => a-b).reverse() : 내림차순
```   

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`every`

```
arr.every() : 모든 원소가 조건에 맞는지 검사하여 맞으면 true 아니면 false
```    

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`slice`

```
arr.slice(start, end) : start idx 부터 end 전 idx 까지 배열 반환
```    