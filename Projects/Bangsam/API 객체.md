<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `API 객체 of Bangsam Project`

<br>


* **설명**
* **선언**
* **사용**

<br>


> 설명

```
js-cookie 와 axios 를 활용
모드를 development 와 product 를 구분하여 선언
```
<br>
<br>

> 선언

```javascript
import axios from "axios";
import Cookie from "js-cookie";

// 객체 만들기
const instance = axios.create({
  baseURL:
    process.env.NODE_ENV === "development"
      ? "http://127.0.0.1:8000/api/v1"
      : "https://backend.{방삼 url}/api/v1",
  withCredentials: true,
});
```
<br>
<br>

> 사용

<br>

## &nbsp;&nbsp;`get`
```javascript
export const getUserInfo = () =>
  instance.get("users/me/").then((response) => response.data);
```

<br>

## &nbsp;&nbsp;`post`<br>
&nbsp;&nbsp;&nbsp; headers 에 csrftoken Cookie 설정
```javascript
export const login = ({ username, password }) => {
  return instance.post(
    "users/login/",
    { username, password },
    {
      headers: {
        "X-CSRFToken": Cookie.get("csrftoken") || "",
      },
    }
  );
};
```