<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `_document.tsx 를 알아보자`

<br>


* **정의**
* **역할**
* **코드**

<br>

> 정의

```
Next.js 프레임워크에서 
사용되는 커스텀 문서 파일

이 파일은 서버에서 렌더링될 때 한 번만 실행

모든 페이지에 공통적으로 적용되는 
HTML 문서의 초기 상태를 정의하는 데 사용
```

<br>
<br>

> 역할

<br>

## &nbsp;&nbsp;`1 )`
```
초기 HTML, 헤드 태그, 바디 태그 등을 설정
```
<br>

## &nbsp;&nbsp;`2 )`
```
서버 측 렌더링 시에만 실행되며, 
클라이언트 측에서는 무시
```
<br>

## &nbsp;&nbsp;`3 )`
```
외부 스타일시트와 스크립트를 추가 가능
```
<br>

## &nbsp;&nbsp;`4 )`
```
렌더링 중에 변경되지 않는 컨텐츠를 정의 가능
```
<br>

## &nbsp;&nbsp;`5 )`
```
페이지의 레이아웃 구조를 설정 가능
```

<br>
<br>


> 코드

<br>

```javascript
import Document, { Html, Head, Main, NextScript } from 'next/document';

class MyDocument extends Document {
  render() {
    return (
      <Html>
        <Head>
          {/* ⭐외부 스타일시트, 메타 태그, 스크립트 등을 추가할 수 있습니다⭐ */}
        </Head>
        <body>
          <header>
            {/* 헤더 내용 */}
          </header>

          <Main />

          <footer>
            {/* 푸터 내용 */}
          </footer>

          <NextScript />
        </body>
      </Html>
    );
  }
}

export default MyDocument;
```

```
* Main

페이지 컴포넌트의 실제 내용이 
<Main> 컴포넌트의 자식으로 들어감


* NextScript

Next.js의 내장 스크립트를 포함하는데 사용

페이지 전환 및 데이터 로딩과 관련된 
클라이언트 측 코드가 포함
```