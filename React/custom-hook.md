> useDidMountEffect

```
마운트 된 후에만 수행하고 
후속 리렌더링이 아닌 경우에 사용 가능
```

```javascript
import { useEffect, useRef } from "react";

function usePrevious(value) {
    const ref = useRef(0);

    useEffect(() => {
        ref.current = value;
    }, [value])

    return ref.current;
}
```

> useToggle

```
부울 값을 전환하는 쉬운 방법을 제공
```

```javascript
import { useState, useCallback } from "react";

function useToggle(initialValue) {
    const [value, setValue] = useState(initialValue);
    const toggleValue = useCallback(() => setValue(v => !v));

    return [value, toggleValue];
}
```

> useInterval

```
간격을 설정하고 컴포넌트가 
언마운트된 후 지우는 데 사용
```

```javascript
import { useEffect, useRef } from "react";

function useInterval(callback, delay) {
    const savedCallback = useRef();

    useEffect(() => {
        savedCallback.current = callback;
    })

    useEffect(() => {
        function tick() {
            savedCallback.current();
        }
        if(delay != null) {
            let id = setInterval(tick, delay);
            return () => clearInterval(id);
        }
    }, [delay]);
}
```

> useInterval

```
상태를 로컬 저장소에 동기화하므로 
브라우저 세션 간에 지속
```

```javascript
import { useState, useEffect } from "react";

function useInterval(callback, delay) {
    const [value, setValue] = useState(() => {
        const jsonValue = localStorage.getItem(key);
        if(jsonValue != null) localStorage.getItem(key);
        if(typeof initialValue === "function") return initialValue();
        return initialValue;
    })

    useEffect(() => {
        localStorage.setItem(key, JSON.stringfy(value))
    }, [key, value]);
}
```

> useLoginStatus

```
로그인을 위한 사용자 정의 후크
```

```javascript
import { useState, useEffect } from 'react';
import axios from 'axios';

function useLoginStatus() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [user, setUser] = useState(null);

  async function login(username, password) {
    try {
      const response = await axios.post('/api/login', { username, password });
      setUser(response.data);
      setIsLoggedIn(true);
    } catch (error) {
      console.error("Failed to login:", error);
    }
  }

  async function logout() {
    try {
      await axios.post('/api/logout');
      setUser(null);
      setIsLoggedIn(false);
    } catch (error) {
      console.error("Failed to logout:", error);
    }
  }

  // Check login status on mount
  useEffect(() => {
    async function checkLoginStatus() {
      try {
        const response = await axios.get('/api/user');
        setUser(response.data);
        setIsLoggedIn(true);
      } catch (error) {
        console.error("Failed to check login status:", error);
      }
    }

    checkLoginStatus();
  }, []);

  return { isLoggedIn, user, login, logout };
}

// 사용
const { isLoggedIn, user, login, logout } = useLoginStatus();
```