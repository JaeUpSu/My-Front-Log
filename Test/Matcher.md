<img src="../Image/testcodeLogo.jpeg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Matchers 를 알아보자 (at React)`

<br>


* **정의**
* **Jest**
* **RTL**

<br>

> 정의

<br>

```
Jest와 RTL 두 라이브러리 모두에서 사용 가능 

하지만 각 라이브러리는 
자체적으로 몇 가지 고유한 Matchers를 제공

expect 함수와 함께 사용
```

<br><br>

> Jest

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toBe`
```
값의 정확한 일치 여부를 확인
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toEqual`
```
값을 재귀적으로 비교하여 
객체나 배열의 일치 여부를 확인
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toMatch`
```
정규 표현식과 문자열을 비교하여 
일치 여부를 확인
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toContain`
```
배열 또는 문자열에 특정 요소 또는 
하위 문자열이 포함되어 있는지 확인
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toThrow`
```
함수가 예외를 throw하는지 확인
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`CODE`
```javascript
test('두 값이 정확히 일치하는지 확인하기', () => {
  expect(2 + 2).toBe(4);
});

test('배열에 특정 요소가 포함되어 있는지 확인하기', () => {
  const numbers = [1, 2, 3, 4, 5];
  expect(numbers).toContain(3);
});

test('함수가 예외를 throw하는지 확인하기', () => {
  const throwError = () => {
    throw new Error('예외 발생');
  };
  expect(throwError).toThrow('예외 발생');
});
```

<br>
<br>

> RTL

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toBeInTheDocument`
```
DOM에 요소가 존재하는지 확인
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toHaveTextContent`
```
요소의 텍스트 콘텐츠가 주어진 값과 일치하는지 확인
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toBeVisible`
```
요소가 화면에 보이는지 확인
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toHaveClass`
```
요소가 특정 클래스를 가지고 있는지 확인
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`toHaveStyle`
```
요소가 특정 스타일 속성을 가지고 있는지 확인
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`CODE`
```javascript
import { render, screen } from '@testing-library/react';
import MyComponent from './MyComponent';

test('특정 텍스트를 가진 요소가 화면에 보이는지 확인하기', () => {
  render(<MyComponent />);
  expect(screen.getByText('Hello, World!')).toBeVisible();
});

test('요소가 특정 클래스를 가지고 있는지 확인하기', () => {
  render(<MyComponent />);
  expect(screen.getByTestId('my-element')).toHaveClass('active');
});

test('요소에 특정 스타일 속성이 있는지 확인하기', () => {
  render(<MyComponent />);
  expect(screen.getByTestId('my-element')).toHaveStyle({ color: 'red', fontSize: '16px' });
});
```