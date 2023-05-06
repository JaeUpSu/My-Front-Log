<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `let & const 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**

<br>

> 정의

```
두 가지 새로운 변수 선언 키워드

let
    블록 스코프를 가지는 변수를 선언하는 키워드
    
const
    let과 유사
    But, 선언 시에 초기값을 할당
    이후에 변경할 수 없는 상수를 선언하는 키워드
```
블록 스코프 => 중괄호 { } 내에서 변수의 유효 범위가 <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;제한되는 것을 의미

<br>

> 사용법

<br>

```
// 초기값 없이 선언
let variableName; 

// 초기값을 포함하여 선언
let variableName = value; 

// 초기값과 함께 선언
const constantName = value; 
```

<br>

> 사용이유


```
* 블록 스코프
    let과 const는 블록 스코프를 가짐

* 재할당 가능성
    let은 재할당이 가능한 변수를 선언할 때 
    사용

    const는 상수를 선언하여 재할당을 금지하고 
    값의 변화를 방지

* 가독성과 유지보수성
    let과 const를 사용하면 코드의 의도를 
    명확하게 표현
```
<br>