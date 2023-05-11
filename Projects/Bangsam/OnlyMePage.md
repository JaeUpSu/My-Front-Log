<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `OnlyMePage of Bangsam Project`

<br>


* **설명**
* **기능**
* **컴포넌트**

<br>


> 설명

```
useUser 을 통한 MyPage Validate Component
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp;`MyPage Validate Component`<br>
 &nbsp;&nbsp;&nbsp; 로그인 여부, 동일한 사용자인지 확인하여 Error 설정
```javascript
  useEffect(() => {
    if (!userLoading) {
      if (isLoggedIn) {
        if (user?.username != userName) {
          navigate("/errorpage");
        }
      } else {
        navigate("/errorpage");
      }
    }
  }, [userLoading, isLoggedIn, user]);
  if (!userLoading) {
    return <>{children}</>;
  } else {
    return <Loading />;
  }
```
<br>
<br>

> 컴포넌트

<br>

 &nbsp;&nbsp; &nbsp;`OnlyMePage.jsx`
```javascript
import { useEffect } from "react";
import { useNavigate, useParams } from "react-router-dom";
import useUser from "../../hooks/useUser";
import Loading from "../Loading/Loading";

// URL 에 userName 포함한 경우 사용
export default function OnlyMePage({ children }) {
  const { isLoggedIn, userLoading, user } = useUser();
  const { userName } = useParams();
  const navigate = useNavigate();
  useEffect(() => {
    if (!userLoading) {
      if (isLoggedIn) {
        if (user?.username != userName) {
          navigate("/errorpage");
        }
      } else {
        navigate("/errorpage");
      }
    }
  }, [userLoading, isLoggedIn, user]);
  if (!userLoading) {
    return <>{children}</>;
  } else {
    return <Loading />;
  }
}
```