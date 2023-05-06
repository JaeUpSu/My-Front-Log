<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Template Literals 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**
* **예시 코드**

<br>
<br>

> 정의 

```
문자열을 보다 편리하게 
작성할 수 있도록 하는 기능

(` ` - 백틱)

문자열 내에서 
변수나 표현식을 쉽게 삽입
여러 줄로 구성된 문자열을 작성 가능
```
<br>
<br>

> 사용법


```
const variable = "value";
const expression = `This is a template literal with ${variable} and ${2 + 2}.`;
```
<br>
<br>

> 사용이유

```
* 변수 및 표현식 삽입

* 여러 줄 문자열 작성

* 문자열 템플릿화
```
<br>
<br>

> 예시 코드

<br>

&nbsp;&nbsp;`변수 및 표현식 삽입`
```
const name = "John";
const age = 30;
const greeting = `Hello, my name is ${name} and I'm ${age} years old.`;

console.log(greeting); // 출력: Hello, my name is John and I'm 30 years old.
```
&nbsp;&nbsp;`여러 줄 문자열 작성`
```
const message = `
  This is a template literal
  with multiple lines
  using backticks.
`;

console.log(message);
/* 출력:
  This is a template literal
  with multiple lines
  using backticks.
*/
```
&nbsp;&nbsp;`문자열 템플릿화`
```
function generateEmail(subject, recipient) {
  return `
    Dear ${recipient},

    I hope this email finds you well. I wanted to reach out regarding ${subject}.

    Best regards,
    John
  `;
}

const email = generateEmail("Meeting", "Alice");
console.log(email);
/* 출력:
  Dear Alice,

  I hope this email finds you well. I wanted to reach out regarding Meeting.

  Best regards,
  John
*/

```

