<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Module 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**

<br>

> 정의 

<br>

&nbsp; `Import & Export`
```
독립적이고 재사용 가능한 단위로 
구성하는 기능을 제공

코드를 캡슐화

전역 스코프 오염을 방지
코드의 구성과 의존성을 명확

코드를 파일 단위로 구성
파일 내에서 변수, 함수, 클래스 등을 
내보내고 가져오는 기능
```
<br>

&nbsp; `Import`

```
모듈 가져오기
다른 모듈에서 기능을 가져와 사용
```
<br>

&nbsp; `Export`

```
모듈 내보내기
모듈에서 사용 가능한 기능을 외부에 공개
```
<br>
<br>

> 사용법

<br>

&nbsp; `Import`

```
import { add, subtract } from "./math.js";

// 출력: 8
console.log(add(5, 3)); 

// 출력: 3
console.log(subtract(10, 7)); 
```
<br>

&nbsp; `Export`

```
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

<br>
<br>

> 사용이유


```
* 코드 분리와 구조화

* 전역 스코프 오염 방지

* 코드 재사용
```
<br>