<img src="../Image/ts.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `인터페이스를 알아보자`

<br>


* **정의**
* **사용이유**
* **기능**

<br>

> 정의


```
[Interface] 특정 유형에 대한 계약을 정의하는 방법
```

<br>

> 사용이유

```
인터페이스는 코드 구성, 유형 검사, 
코드 재사용성, 문서화 및 IDE 지원을 개선하는 데 
도움이 되는 TypeScript의 강력한 도구

효과적으로 사용하면
보다 유지 관리 가능하고 
확장 가능하며 오류가 없는 코드 설계 가능
```

<br>

> 기능

<br>

- 개체 모양
- 함수 모양
- 확장
- 선택적 속성
- 읽기 전용 속성
- 자동완성

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`개체 모양` &nbsp;&nbsp;  속성 및 유형을 포함하여 개체의 모양을 정의
```
interface Person {
  name: string;
  age: number;
}

const Kim: Person = {
  name: "Kim",
  age: 28
};

const Lee: Person = {
  name: "Lee",
  age: "!%!#@" // Error
};
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`함수 모양` &nbsp;&nbsp;  매개변수 및 반환 유형을 포함하여 함수의 모양을 정의
```
interface Hello {
  (name: string): string;
}

const hello: Hello = (name: string) => `Hello, ${name}!`;

console.log(hello("Kim"));   

---
출력 : Hello, Kim!
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`확장 extends` &nbsp;&nbsp;  다른 인터페이스를 확장하여 속성을 상속하고<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 새 속성을 추가 가능
```
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  jobTitle: string;
}

const kim: Employee = {
  name: "Kim",
  age: 28,
  jobTitle: "FE Developer"
};
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`선택적 속성 ?` &nbsp;&nbsp;  객체에 존재할 수도 있고 존재하지 않을 수도 있는 <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 선택적 속성을 정의 가능
```
interface Person {
  name: string;
  age?: number;
}

const kim: Person = {
  name: "Kim",
  age: 28
};

const lee: Person = {
  name: "Lee"
};
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`읽기 전용 속성 readonly` &nbsp;&nbsp;  설정된 후에 수정할 수 없는 속성을 정의 가능
```
interface Person {
  readonly name: string;
  age: number;
}

const alice: Person = {
  name: "Alice",
  age: 30
};

alice.age = 31;        // OK
alice.name = "Alicia"; // Error
```
<br>


&nbsp;&nbsp;&nbsp;&nbsp;`자동완성` &nbsp;&nbsp;  최신 코드 편집기 및 IDE (통합 개발 환경) 에서 자동 완성 가능
```
interface Person {
  name: string;
  age: number;
}

const kim: Person = {
  name: "Kim",
  age: 30
};

// 아래 kim + '.' 을 입력하면 자동완성 가능
console.log(kim.name);
```
<br>

