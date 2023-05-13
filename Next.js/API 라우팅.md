<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `API 라우팅을 알아보자`

<br>


* **정의**
* **설명**
* **코드**

<br>

> 정의

```javascript
pages/api 디렉토리를 사용하여 API 라우트를 생성
```
<br>
<br>

> 설명

``` 
msw 를 사용하지 않고 
Next.js 에서는 API 라우트를 사용

클라이언트와 서버 간에 
데이터를 주고받기 위한 
엔드포인트를 정의하는 것

클라이언트의 HTTP 요청을 처리
데이터베이스에 접근하거나 
외부 서비스와 통신하여 필요한 데이터를 반환

GET, POST, PUT, DELETE 등 
경로를 사용하여 요청을 처리
```

<br>
<br>

> 코드

<br>

```javascript
// pages/api/users.js

export default function handler(req, res) {
  const users = [
    { id: 1, name: 'John Doe' },
    { id: 2, name: 'Jane Smith' },
  ];

  res.status(200).json(users);
}
```