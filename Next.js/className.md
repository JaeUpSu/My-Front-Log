<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `className 을 알아보자`

<br>


* **정의**
* **유의사항**
* **코드**

<br>

> 정의

``` 
className은 React 컴포넌트에서 
HTML 요소의 클래스를 지정하는 데 사용되는 속성
```

<br>
<br>

> 유의사항

<br>

## &nbsp;&nbsp;`클래스 이름 중복 회피`
```
클래스 이름은 고유해야 하므로 
중복을 피해야 함

이를 위해 클래스 이름에는 
일반적으로 컴포넌트 이름이나 
BEM(Block Element Modifier) 방식과 같은 
네이밍 규칙을 따르는 것이 좋음
```
<br>

## &nbsp;&nbsp;`조건부 클래스 지정`
```
동일한 콘텐츠에 대한 
반복적인 서버 요청을 피할 수 있음

(if/else, 삼항 연산자 등)을 활용하여 
동적으로 className을 설정 가능
```
<br>

## &nbsp;&nbsp;`CSS Modules 사용`
```
CSS Modules을 지원하여 
CSS 클래스를 모듈화하고 컴포넌트와 연결

CSS Modules을 사용하면 
클래스 이름이 자동으로 고유화되어 충돌을 방지
```

<br>
<br>

> 코드

<br>

## &nbsp;&nbsp;`CSS Modules 사용`<br>
&nbsp;&nbsp;MyComponent 컴포넌트 스타일 정의<br>
&nbsp;&nbsp;styles 객체에 할당
```javascript
import styles from './MyComponent.module.css';

const MyComponent = ({ isActive }) => {
  const classNames = `${styles.container} ${isActive ? styles.active : ''}`;

  return <div className={classNames}>Hello, World!</div>;
};

export default MyComponent;
```