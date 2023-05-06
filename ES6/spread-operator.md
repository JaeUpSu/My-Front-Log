<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Spread Operator 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**

<br>

> 정의 

```
... 기호로 표시

배열이나 객체의 요소를 복사하거나 
병합하는데 사용되는 문법적인 기능

Spread Operator를 사용하면 
배열이나 객체의 요소를 펼쳐서 
개별적인 요소로 확장
```
<br>
<br>

> 사용법

<br>

&nbsp; `배열 요소 확장`

```
const newArray = [...array];
```
<br>

&nbsp; `객체 속성 확장`

```
const newObject = { ...object };
```
<br>
<br>

> 사용이유


```
* 배열과 객체의 요소를 복사
       ㄴ> 원본을 변경하지 않고 
           안전하게 요소를 복사
        
        // 배열 요소 복사
        const copiedNumbers = [...numbers];

        // 배열 요소 확장
        const mergedNumbers = [...numbers, 4, 5];
         

* 배열과 객체의 요소를 병합
       ㄴ> 배열을 결합하거나 
           객체의 속성을 확장 가능

        // 객체 속성 확장
        const extendedPerson = { ...person, city: "New York" };


* 함수 호출 시 인수 전달
       ㄴ> 배열을 개별적인 인수로 전달 가능 
           가변 인자 함수에 유용하게 사용

        const result = sum(...numbers); 
```
<br>