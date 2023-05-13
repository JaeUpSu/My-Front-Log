<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `NextScript 를 알아보자`

<br>


* **정의**
* **설명**
* **장점**
* **코드**

<br>

> 정의

```javascript
class NextScript extends React.Component<NextScriptProps> {}
```
<br>
<br>

> 설명

``` 
_document.js 파일에서 사용

HTML 문서에 Next.js에 필요한 스크립트를 
자동으로 추가해주는 역할

NextScriptProps
 ㄴ> NextScript 컴포넌트의 속성(props) 타입
```

<br>
<br>

> 장점

<br>

## &nbsp;&nbsp;`자동 스크립트 인클루드`
``` 
Next.js에서 필요한 스크립트를 자동으로 포함

이는 개발자가 수동으로 
스크립트를 추가하거나 관리할 필요가 없다는 
장점을 제공
```
<br>

## &nbsp;&nbsp;`최적화된 로딩`
``` 
페이지를 자동으로 최적화
필요한 스크립트를 청크(chunk) 단위로 분할 로딩

이는 초기 로딩 속도를 향상
성능을 최적화하는데 도움
```
<br>

## &nbsp;&nbsp;`SSR 지원`
``` 
서버 사이드 렌더링(SSR)을 위해 
필요한 스크립트를 자동으로 처리

이는 클라이언트와 서버 간의 일관성을 유지

SSR에 필요한 스크립트를 
적절하게 처리하는데 도움
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
      <Html lang="en">
        <Head>
          {/* Additional meta tags, stylesheets, etc. */}
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}

export default MyDocument;
```