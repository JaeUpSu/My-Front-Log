<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `ErrorPage 를 알아보자`

<br>


* **정의**
* **설명**
* **사용법**

<br>

> 정의

```javascript
pages 디렉토리 내에 _error.js 파일을 생성
ErrorPage 컴포넌트를 정의
```


<br>
<br>

> 설명

``` 
ErrorPage는 애플리케이션에서 
발생하는 오류를 처리

사용자에게 적절한 에러 페이지를 
보여주는데 사용
```

<br>
<br>

> 사용법

<br>

```javascript 
import ErrorPage from 'next/error';

const CustomErrorPage = ({ statusCode }) => {
  return <ErrorPage statusCode={statusCode} />;
};

export default CustomErrorPage;
```
<br>

## &nbsp;&nbsp;`에러 정보 확인`
```javascript 
CustomErrorPage.getInitialProps = ({ res, err }) => {
  const statusCode = res ? res.statusCode : err ? err.statusCode : 404;
  return { statusCode };
};
```
<br>

## &nbsp;&nbsp;`특정 에러페이지`
```javascript 
const CustomErrorPage = ({ statusCode }) => {
  if (statusCode === 404) {
    // 404 에러 페이지 커스터마이즈
    return <h1>Page Not Found</h1>;
  }

  return <ErrorPage statusCode={statusCode} />;
};
```
<br>
