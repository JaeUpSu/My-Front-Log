<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `ReactDjango Linking of MyInfo Project`

<br>


* **설명**
* **구현**

<br>


> 설명

```
Front 에서 React
Back 에서 DJango  

연결
```

&nbsp;&nbsp;`CORS`
```
웹 애플리케이션의 도메인이 
다른 도메인으로부터 리소스를 요청할 때 

브라우저의 보안 정책에 따라 
제약이 발생하는 것을 
우회하기 위한 메커니즘
```

&nbsp;&nbsp;`CSRF`
```
웹 애플리케이션의 사용자가 
의도하지 않은 요청을 처리하는 
보안 취약점을 방지하기 위한 기능
```

<br>
<br>

> 구현

<br>

### &nbsp;&nbsp;`* Front`

```
npm install axios
```

### &nbsp; *index.js*<br>
&nbsp; - config settings
```javascript
import axios from "axios";

axios.defaults.xsrfCookieName = "csrftoken";
axios.defaults.xsrfHeaderName = "X-CSRFToken";
axios.defaults.withCredentials = true;
```
<br>

### &nbsp; *RequestPost.js*<br>
&nbsp; - request post using axios api
```javascript
import axios from "axios";

const RequestPost = (context) => {
  axios
    .post("http://127.0.0.1:8000/api/v1/users/", {
      name: context.name,
      tel: context.tel,
      email: context.email,
      request: context.request,
      created: new Date(),
    })
    .then((response) => {
      console.log(response);
    })
    .catch((error) => {
      console.log(error);
    });
};

export default RequestPost;
```
<br>


### &nbsp;&nbsp;`* Back`

### &nbsp; *settings.py*<br>
&nbsp; - CORS Settings
```python

...

INSTALLED_APPS = [
    "corsheaders",
    ...
]
...

MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    ...
]
```
...<br><br>
`CORS_ORIGIN_WHITELIST`<br>
React 애플리케이션이 실행되는 도메인을 명시<br>
CORS를 허용하도록 설정
```
CORS_ORIGIN_WHITELIST = ['http://127.0.0.1:8000',
                         'http://localhost:3000']
```
<br>

`CORS_ALLOW_CREDENTIALS`<br>
True로 설정되어 있어, 요청에 대한 <br>
인증 정보(cookies 등)를 서버에 전송
```
CORS_ALLOW_CREDENTIALS = True
```
<br>

`CORS_ORIGIN_ALLOW_ALL`<br>
True로 설정되어 있어, <br>
모든 도메인에서의 CORS 요청을 허용
```
CORS_ORIGIN_ALLOW_ALL = True
```

<br>

`CSRF_COOKIE_SAMESITE`<br>
None으로 설정되어 있어, <br>
CSRF 쿠키의 SameSite 속성을 None으로 설정
```
CSRF_COOKIE_SAMESITE = None
```


<br>

`CORS_ALLOW_HEADERS`<br>
요청 헤더에 포함되는 허용된 헤더들의 목록을 정의
```
CORS_ALLOW_HEADERS = (
    'access-control-allow-credentials',
    'access-control-allow-origin',
    'access-control-request-method',
    'access-control-request-headers',
    'accept',
    'accept-encoding',
    'accept-language',
    'authorization',
    'connection',
    'content-type',
    'dnt',
    'credentials',
    'host',
    'origin',
    'user-agent',
    'x-requested-with',
)
```


<br>
<br>
