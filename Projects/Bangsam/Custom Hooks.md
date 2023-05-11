<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Custom Hooks of Bangsam Project`

<br>


* **설명**
* **선언**
* **사용**

<br>


> 설명

```
React에서 상태 관리, 비동기 작업, 
라이프사이클 이벤트 등을 추상화하여 
재사용 가능한 로직을 정의하는 기능

Hooks는 "use"라는 접두사로 시작
useState, useEffect, useContext 등의 
기본 Hooks를 사용
```
<br>
<br>

> 선언

<br>

## &nbsp;&nbsp;`useUser`<br>
&nbsp;&nbsp;&nbsp; Login 의 유무로 사용되는 user Hook
```javascript
import { useQuery } from "@tanstack/react-query";
import { getUserInfo } from "../services/api";

export default function useUser() {
  const { isLoading, data, isError } = useQuery(["me"], getUserInfo, {
    retry: false,
    refetchOnWindowFocus: false,
  });
  
  return {
    userLoading: isLoading,
    user: data,
    isLoggedIn: !isError,
  };
}
```

<br>

## &nbsp;&nbsp;`useDidMountEffect`<br>
&nbsp;&nbsp;&nbsp; 컴포넌트가 마운트된 이후에만 콜백 함수 실행
```javascript
import { useRef, useEffect } from "react";

export const useDidMountEffect = (callback, deps) => {
  const didMount = useRef(false);

  useEffect(() => {
    if (didMount.current) callback();
    else didMount.current = true;
  }, deps);
};
```

<br>

## &nbsp;&nbsp;`useInfiniteScroll`<br>
&nbsp;&nbsp;&nbsp; UI 에 맞춰 필요한 만큼만 데이터 쿼리 Fetch<br>
&nbsp;&nbsp;&nbsp; scroll event 로 fetching

### &nbsp;&nbsp;&nbsp;[**🔗 무한 스크롤**][infinteScrollLink]<br>

[infinteScrollLink]: https://github.com/JaeUpSu/My-Front-Log/blob/main/Projects/Bangsam/%EB%AC%B4%ED%95%9C%EC%8A%A4%ED%81%AC%EB%A1%A4.md "Go Bangsam useInfinteScroll"
<br>
<br>
<br>

> 사용

<br>

## &nbsp;&nbsp;`useUser`<br>
```javascript
const { user, isLoggedIn, userLoading } = useUser();
```

<br>

## &nbsp;&nbsp;`useDidMountEffect`<br>
```javascript
import React, { useState } from 'react';
import useDidMountEffect from './useDidMountEffect';

function MyComponent() {
  const [count, setCount] = useState(0);

  useDidMountEffect(() => {
    console.log('Component did mount');
  }, []);

  useDidMountEffect(() => {
    console.log('Count changed:', count);
  }, [count]);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <p>Count: {count}</p>
    </div>
  );
}

export default MyComponent;
```



