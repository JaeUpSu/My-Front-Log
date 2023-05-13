<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Dynamic Module of ReactMaster Project`

<br>


* **정의**
* **기능**

<br>


> 정의

```
next/dynamic을 사용하면 필요한 경우에만 
클라이언트 측에서 모듈을 로드할 수 있어 
초기 로딩 속도를 개선 가능

또한 코드 스플리팅을 통해 
필요하지 않은 모듈의 로딩을 방지

필요한 모듈이 클라이언트 측에서만 실행
```
<br>
<br>

> 기능

<br>

```javascript
import dynamic from 'next/dynamic';

const DynamicComponent = dynamic(() => import('./MyComponent'), {
  loading: () => <div>Loading...</div>,
});

function MyPage() {
  return (
    <div>
      <h1>My Page</h1>
      <DynamicComponent />
    </div>
  );
}
```