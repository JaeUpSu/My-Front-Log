<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Class 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**

<br>

> 정의

```
템플릿(template) 역할

JavaScript에서 객체 지향 프로그래밍을 
구현하기 위한 문법적인 개념

객체를 생성하고 관련 메서드와 
속성을 그룹화하여 보다 
구조적인 코드를 작성

속성(fields)과 메서드(methods)로 구성
```
<br>

> 사용법

<br>

- class 키워드를 사용
- 클래스 이름은 대문자
- constructor(생성자) 메서드<br>
  또는 다른 메서드 정의
    
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`정의`

```
class MyClass {
  constructor(param1, param2) {
    this.param1 = param1;
    this.param2 = param2;
  }
  method1() {
    // 메서드 동작 정의
  }
  method2() {
    // 메서드 동작 정의
  }
}
```
    
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`사용`

```
const myObject = new MyClass(arg1, arg2); 
// 클래스로부터 객체 생성

myObject.method1(); // 메서드 호출
myObject.method2(); // 메서드 호출
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`상속`

```
class MySubclass extends MyClass {
  constructor(param1, param2, param3) {
    // 부모 클래스의 생성자 호출
    super(param1, param2); 
    this.param3 = param3;
  }

  // 추가적인 메서드 정의
}

```
<br>

> 사용이유


```
코드를 재사용
유지보수하기 쉽게 생성 가능
객체의 속성과 메서드를 캡슐화 => 구조화
```
<br>