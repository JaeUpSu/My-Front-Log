<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `GlobalStyle of ReactMaster Project`

<br>


* **정의**
* **GlobalStyle**
* **ThemeProvider**

<br>


> 정의

```
ReactMaster 에서
전역으로 사용되는 GlobalStyle

해당 GlobalStyle 을 
ThemeProvider 에 적용하여 Custom 하게 생성
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp; `theme.ts`<br>
&nbsp;&nbsp; &nbsp; GlobalStyle 선언
```javascript
import { createGlobalStyle } from "styled-components";

export const GlobalStyle = createGlobalStyle`
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;400&display=swap');
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, menu, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
main, menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, main, menu, nav, section {
  display: block;
}
/* HTML5 hidden-attribute fix for newer browsers */
*[hidden] {
    display: none;
}
body {
  line-height: 1;
}
menu, ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
  content: '';
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
* {
  box-sizing: border-box;
}
body {
  font-family: 'Source Sans Pro', sans-serif;
  background-color:${(props) => props.theme.bgColor};
  color:${(props) => props.theme.textColor}
}
a {
  text-decoration:none;
  color:inherit;
}
`;
```

<br>

## &nbsp;&nbsp; `ThemeProvider.tsx`<br>
&nbsp;&nbsp; &nbsp; _app.tsx 에 적용할 ThemeProvider 선언
```javascript
import { ThemeProvider as StyledThemeProvider } from "styled-components";
import { useRecoilState } from "recoil";
import { lightTheme, darkTheme } from "@/styles/theme";
import { isDarkAtom } from "../atom";
import { GlobalStyle } from "@/styles/theme";

type AppProps = {
  children: React.ReactNode;
};

export const ThemeProvider = ({ children }: AppProps) => {
  const [isDark, setIsDark] = useRecoilState(isDarkAtom);
  const handleTheme = () => setIsDark((_isDark) => !_isDark);

  return (
    <StyledThemeProvider theme={isDark ? darkTheme : lightTheme}>
      <GlobalStyle />
      <button onClick={handleTheme}>Theme Change</button>
      {children}
    </StyledThemeProvider>
  );
};
```