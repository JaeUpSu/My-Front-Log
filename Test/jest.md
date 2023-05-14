<img src="../Image/jest.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `jest 를 알아보자 (at React)`

<br>


* **정의**
* **설명**
* **장점**
* **방법**
* **추가 팁**

<br>

> 정의

<br>

```
npm install jest
```
```
JavaScript를 위한 강력한 테스트 프레임워크
Front-end 개발자들에게 널리 사용

Jest는 코드 품질을 유지
소프트웨어의 신뢰성을 높이기 위해 
테스트 작성, 실행 및 관리를 지원
```
<br><br>

> 설명

```
테스트 작성, 실행 및 결과 분석을 위한 도구를 제공하는 테스트 프레임워크

테스트 코드를 작성하여 
소프트웨어의 기능을 테스트하고 
예상 동작과 실제 동작을 비교

버그를 찾고 수정하는 데 사용

Jest는 단위 테스트, 통합 테스트, 
스냅샷 테스트, 비동기 코드 테스트 등 
다양한 유형의 테스트를 지원
```

<br><br>

> 장점

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`간편한 구성 및 사용`
```
사용하기 쉬운 구문과 내장된 기능을 제공
테스트 작성을 단순화
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`강력한 Matchers`
```
다양한 Matchers 함수를 사용하여 
예상 동작을 검증하고 테스트 결과를 비교
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`자동 Mocking`
```
자동으로 모듈과 함수의 Mock을 생성
의존성을 가진 코드를 테스트하기 용이
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`코드 커버리지 분석`
```
테스트를 실행하면서 코드 커버리지를 분석
테스트된 코드의 품질을 측정
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`비동기 테스트 지원`
```
비동기 코드를 테스트하기 위한 
다양한 방법과 도구를 제공

테스트 작성을 간편
```

<br><br>

> 방법

<br>

&nbsp;&nbsp;`1 )`
```
Node.js 환경에서 실행되며, 
npm 또는 yarn을 통해 설치
```

<br>

&nbsp;&nbsp;`2 )`
```
테스트 파일을 작성하고, 
describe와 it 함수를 사용하여 
테스트 스위트와 테스트 케이스를 구성
```

<br>

&nbsp;&nbsp;`3 )`
```
expect 함수와 Jest의 
많은 Matchers 함수들을 사용

예상 동작을 검증
```

<br>

&nbsp;&nbsp;`4 )`
```
npm test 또는 yarn test 명령어를 실행하여 
테스트를 실행하고 결과를 확인
```

<br><br>

> 추가 팁

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`Describe & Test Suites`
```
describe 함수를 사용

테스트 스위트를 그룹화
관련된 테스트 케이스를 그룹화하여 
코드의 구조와 의도를 명확하게 전달

블록은 중첩 가능
테스트를 계층적으로 구성하여 
테스트 스위트를 구조화
```


<br>

&nbsp;&nbsp;&nbsp;&nbsp;`Before, After Hooks`
```
beforeEach와 afterEach 함수를 사용
각 테스트 케이스 전후에 실행되는 
코드를 작성 가능 

이를 활용하여 공통적인 설정 또는 
정리 작업을 수행 가능

beforeAll과 afterAll 함수는
테스트 스위트 전후에 
한 번만 실행되는 코드를 작성할 때 사용
```


<br>

&nbsp;&nbsp;&nbsp;&nbsp;`Mocking & Stubbing`
```
모의 객체를 생성
함수의 반환 값을 지정하거나 
호출 여부를 확인하는 기능을 제공

jest.fn()을 사용
함수를 간단하게 목킹하거나 
jest.mock()을 사용하여 
외부 모듈을 모의화 가능

Mock 함수를 사용하여 
외부 종속성을 격리하고, 
테스트에서 예상된 동작을 가정하여 
코드의 다른 부분과 독립적으로 테스트
```


<br>

&nbsp;&nbsp;&nbsp;&nbsp;`Snapshot Testing`
```
스냅샷 테스팅 기능을 사용
컴포넌트 렌더링 결과, JSON 데이터, 
HTML 마크업 등의 스냅샷을 생성하고 저장 가능

향후 변경 사항이 발생했을 때 
스냅샷과 비교하여 예상치 않은 변경을 캐치 가능

코드 변경으로 인한 렌더링 결과의 
예기치 않은 변화를 탐지하는 데 유용

UI 컴포넌트와 같이 정적인 결과를 가지는 요소에 적합
```
