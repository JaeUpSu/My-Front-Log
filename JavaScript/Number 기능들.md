<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Number 의 내장 기능들을 알아보자`

<br>

* **정의**
* **기능**

<br>

> 정의

```
해당 메모들은 JavaScript 에서 
Number 객체의 내장 기능 정리이다.
```
<br>

> 기능

<br>

- MIN_VALUE
- toFixed
    
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`MIN_VALUE`

```
Number.MIN_VALUE : JS 에서 표현할 수 있는 0에 가장 가까운 정수지만 음수는 아닌 수

// 0을 제외한 양수의 최댓값 구할 때 사용하는 듯
```    
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toFixed`

```
{숫자}.toFixed({소수점 길이}) : 해당 {숫자} 를 {소수점 길이} 만큼만 반올림하여 반환

const num = 213.1235;
num.toFixed(3); // 213.124
```    
