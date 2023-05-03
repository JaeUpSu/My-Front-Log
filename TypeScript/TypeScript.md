<img src="../Image/ts.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `TypeScript 를 알아보자`

<br>


* **정의**
* **사용이유**
* **기능**
* **장점**

<br>

> 정의


```
코드 품질을 개선하고 오류를 방지하는 데
도움이 되는 정적으로 유형이 지정된
JavaScript 상위 집합
    
오류를 포착하고 코드를 유지 관리하기 쉽게 만들 수 있습니다. 
이는 개발 프로세스 초기에 보다 깔끔한 코드를 작성하고 
오류를 포착하는 데 도움이 되므로 좋은 출발점입니다.
```


<br/>
<br/>

> 사용 이유


```
"고급 기능과 도구가 필요한 더 크고 복잡한 프로젝트" 에서 Good !! 

JavaScript는 대중적이고 널리 사용되는 프로그래밍 언어이지만 
크고 복잡한 코드베이스를 작성하고 유지하기 어렵게 만드는 
몇 가지 단점이 있습니다. 

# JavaScript의 주요 단점

    - 컴파일 시간에 특정 유형의 오류를 포착하기 어려워 버그가 많음

    - 도구 및 IDE 지원이 부족, 이로 인해 크고 복잡한 코드베이스를 작성하고 
      유지 관리하기가 더 어려워
    
    - 강력한 객체 지향 기능이 없기 때문에 코드를 재사용 가능하고 
      캡슐화된 구조로 구성하기가 더 어려움
      


JavaScript는 동적으로 유형이 지정되는 언어
즉, 변수 유형은 컴파일 타임이 아닌 런타임에 결정

전반적으로 정적 유형 분석은 
특히 크고 복잡한 프로젝트에서 JavaScript 코드의 품질과 
안정성을 향상시키는 강력한 도구 가능
```


<br/>
<br/>

> 기능

<br/>

* Type
    * 인터페이스 ( I n t e r f a c e )
    * 유형 별칭 ( T y p e &nbsp; a l i a s e s )
    * 제네릭 ( G e n e r i c s )

<br/>

<span style="background-color: blue" >* 코드 품질, 유지 관리 및 확장성을 개선<br>* 광범위한 사용 사례 및 요구 사항에 적응할 수 있는 강력하고 유연한 코드</span>

<br/>

`인터페이스` &nbsp; &nbsp;특정 유형에 대한 계약을 정의하는 방법
```
interface User {
  name: string;
  age: number;
  email: string;
}
```
<br>

`유형 별칭` &nbsp; &nbsp; 기존 유형에 대한 새 이름을 정의하는 방법
```
type MyFunction = (a: number, b: number) => number;
```
<br>

`제네릭` &nbsp; &nbsp;다양한 유형과 함께 작동할 수 있는 함수 및 클래스를 정의하는 방법
```
function swap<T>(a: T, b: T): void {
  const temp = a;
  a = b;
  b = temp;
}

let x = 1;
let y = 2;
swap(x, y); // x = 2, y = 1

let str1 = 'hello';
let str2 = 'world';
swap(str1, str2);
```

<br/>
<br/>

* Other
    * 열거형 ( E n u m s )
    * 데코레이터 ( D e c o r a t o r s )

<br/>


<span style="background-color: blue" >* 열거형과 데코레이터는 코드 품질, 유지 관리성 및 유연성을 개선<br>* 더 읽기 쉽고 확장 가능하며 시간이 지남에 따라 유지하기 쉬움</span>

<br>


`열거형` &nbsp; &nbsp; 명명된 상수 집합을 정의하는 방법
```
enum DaysOfWeek {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday
}
```

<br>

`데코레이터` &nbsp; &nbsp; 클래스 및 기타 유형의 동작을 수정하거나 확장하는 방법
```
// 함수를 실행하는 데 걸리는 시간을 기록하는 데코레이터

function logTime(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;

  descriptor.value = function(...args: any[]) {
    const start = Date.now();
    const result = originalMethod.apply(this, args);
    const end = Date.now();

    console.log(`Method ${propertyKey} took ${end - start}ms to run`);
    
    return result;
  };

  return descriptor;
}

class MyClass {
  @logTime
  myMethod() {
    // ...
  }
}
```
<br>
<br/>
<br/>

> 장점


```
코드의 가독성을 높이고, 
오류를 미리 방지하며, 
개발자 간의 협업을 원활하게 함
```


<br/>
<br/>

> Missions


- [ ] 타입스크립트의 기본 문법을 충분히 이해

- [ ] 타입 추론, 제네릭, 인터페이스, 타입 별칭 등의 고급 기능을 이해하고 활용

- [ ] 타입스크립트를 사용하여 안정적이고 유지보수하기 쉬운 코드를 작성

- [ ] 타입 안정성을 유지하기 위해 적극적으로 타입 검사를 수행

- [ ] 타입스크립트를 사용하여 프로젝트를 구성하고 관리
