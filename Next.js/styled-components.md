<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Styled-Components 를 알아보자`

<br>


* **설명**
* **코드**

<br>

> 설명

``` 
'classNameclassName SSR 중에 
생성된 것과 일치하지 않을 수 있습니다.

이 불일치로 인해 경고가 트리거

서버 쪽 렌더링 중에 스타일이 제대로 적용
클라이언트 쪽에서 하이드레이션되도록 함
 => ServerStyleSheet

변경 사항을 적용하려면 
Next.js 개발 서버를 다시 시작
```

<br>
<br>


> 코드

<br>

## &nbsp;&nbsp; `_document.js`
```javascript
import Document from 'next/document';
import { ServerStyleSheet } from 'styled-components';

class MyDocument extends Document {
  static async getInitialProps(ctx) {
    const sheet = new ServerStyleSheet();
    const originalRenderPage = ctx.renderPage;

    try {
      ctx.renderPage = () =>
        originalRenderPage({
          enhanceApp: (App) => (props) => sheet.collectStyles(<App {...props} />),
        });

      const initialProps = await Document.getInitialProps(ctx);
      return {
        ...initialProps,
        styles: (
          <>
            {initialProps.styles}
            {sheet.getStyleElement()}
          </>
        ),
      };
    } finally {
      sheet.seal();
    }
  }
}

export default MyDocument;
```