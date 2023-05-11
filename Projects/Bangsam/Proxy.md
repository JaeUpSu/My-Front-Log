<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Proxy of Bangsam Project`

<br>


* **정의**
* **설명**
* **기능**

<br>


> 정의

```
동일 출처 정책(Same Origin Policy)에 따른 제한을 우회

┌───────────────┐           ┌───────────────┐           ┌───────────────┐
│    Browser    │           │   Development │           │    Backend    │
│               │           │    Server     │           │    Server     │
│               │           │               │           │               │
│               │           │               │           │               │
│   Client      │  Proxy    │   Proxy       │   Server  │    API        │
│   Application │ ────────▶ │   Server      │ ◀───────  │               │
│               │           │               │           │               │
└───────────────┘           └───────────────┘           └───────────────┘
```
<br>


> 설명

```
배포 안했을 때 프록시를 통한 데이터 요청
```

<br>
<br>

> 기능

<br>

 &nbsp;&nbsp; &nbsp;`setupProxy.js`
```javascript
const { createProxyMiddleware } = require("http-proxy-middleware");

module.exports = function (app) {
  app.use(
    "/api/v1",
    createProxyMiddleware({
      target: "https://bangsam.site",
      // target: "http://127.0.0.1:8000",
      changeOrigin: true,
      secure: false,
    })
  );
};
```