<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Styled-Components of ReactMaster Project`

<br>


* **정의**
* **환경설정**
* **props**
* **styled**

<br>


> 정의

```
Next.js 에서 
Styled-Components 를 사용한다면

SSR(서버 쪽 렌더링) 중에 스타일이 
지정된 각 구성 요소에 고유한 해시를 
자동으로 추가하기 때문에 발생

 => Prop `className` did not match.
```
<br>
<br>

> 환경설정

<br>

## &nbsp;&nbsp; `_document.tsx`
```javascript
import Document, {
  Html,
  Head,
  Main,
  NextScript,
  DocumentContext,
} from "next/document";
import { ServerStyleSheet } from "styled-components";

export default class MyDocument extends Document {
  static async getInitialProps(ctx: DocumentContext) {
    const sheet = new ServerStyleSheet();
    const originalRenderPage = ctx.renderPage;

    try {
      ctx.renderPage = () =>
        originalRenderPage({
          enhanceApp: (App) => (props) =>
            sheet.collectStyles(<App {...props} />),
        });

      const initialProps = await Document.getInitialProps(ctx);
      return {
        ...initialProps,
        styles: [initialProps.styles, sheet.getStyleElement()],
      };
    } finally {
      sheet.seal();
    }
  }

  render() {
    return (
      <Html>
        <Head />
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}
```

<br>

## &nbsp;&nbsp; `해석`

<br>

```
const sheet = new ServerStyleSheet();


ServerStyleSheet는 styled-components와 함께 사용되는 
서버 사이드 스타일링 라이브러리
```

<br>

```
const originalRenderPage = ctx.renderPage;


'ctx.renderrenderPage 메서드를 참조

이 코드는 원래의 메서드를 
renderPageoriginalRenderPage 변수에 저장
```

<br>

```
ctx.renderPage = () =>
    originalRenderPage({
      enhanceApp: (App) => (props) =>
        sheet.collectStyles(<App {...props} />),
    });


ctx.renderPage를 오버라이딩하여 
스타일 시트 수집을 위해 enhanceApp 함수를 사용
```

<br>

```
const initialProps = await Document.getInitialProps(ctx);


Document.getInitialgetInitialProps를 실행하고 
초기 속성을 가져옴
```
<br>

```
return {
  ...initialProps,
  styles: [initialProps.styles, sheet.getStyleElement()],
};


이전 단계에서 얻은 초기 속성과 수집된 스타일을 반환

styles 배열은 초기 속성의 스타일과 
수집된 스타일 요소를 함께 포함
```

<br>

```
sheet.seal()


스타일 시트를 봉인하고 재사용을 방지

이 코드는 스타일 시트의 
누수를 방지하기 위해 사용
```


<br>
<br>


> props

```javascript
<ThemeProvider theme={theme}>
  <App />
</ThemeProvider>

  ...

const Item = styled.li`
  margin-right: 20px;
  color: ${(props) => props.theme.white.darker};
  transition: color 0.3s ease-in-out;
  position: relative;
  display: flex;
  justify-content: center;
  flex-direction: column;
  &:hover {
    color: ${(props) => props.theme.white.lighter};
  }
`;

  ...


const Banner = styled.div<{ bgPhoto: string }>`
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 60px;
  background-image: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, 1)),
    url(${(props) => props.bgPhoto});
  background-size: cover;
`; 
 
  ...
  ...
          <Banner
            onClick={incraseIndex}
            bgPhoto={makeImagePath(data?.results[0].backdrop_path || "")}
          >
            <Title>{data?.results[0].title}</Title>
            <Overview>{data?.results[0].overview}</Overview>
          </Banner>
```
<br>
<br>

> styled

```
styled(motion.svg)와 styled.div은 둘 다 
styled-components 라이브러리에서 제공하는 
스타일드 컴포넌트의 문법


styled(motion.svg) 는 
Framer Motion 라이브러리에서 제공하는 
애니메이션 기능을 적용하기 위한 것
```
<br>
<br>