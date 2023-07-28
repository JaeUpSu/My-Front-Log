<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Default Parameters 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**

<br>

> 정의

```
함수의 매개변수에 기본값을 
설정할 수 있는 기능이 도입

함수를 호출할 때 
매개변수를 명시하지 않았을 경우, 
기본값이 자동으로 할당

* 함수의 유연성을 높임
* 코드를 간결하게 작성 가능
```
<br>

> 사용법

<br>

- 할당된 기본값은 해당 매개변수가 <br>undefined인 경우에만 적용

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`정의`

```

function myFunction (param1 = default1, param2 = default2) {
  // 함수 동작 정의
}


function greet(name = "Guest") {
  console.log("Hello, " + name);
}

greet(); // 출력: Hello, Guest
greet("John"); // 출력: Hello, John
```

<br>

> 사용이유


```
* 코드의 가독성과 유지보수성을 향상

* 발생할 수 있는 에러와 
  예외 상황을 방지하는 데 도움
```
<br>
