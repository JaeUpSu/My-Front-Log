## 🪵 [React-Hooks] useEffect

<hr>

<br>

> 컴포넌트애서 `Side Effect` 를 실행하는 내장 후크

> `데이터 가져오기, 구독 또는 DOM 수동 변경` 등

> 마운트 시 한번 실행

> 마운트 시 종속성 변경될 때마다 실행

> 마운트 해제 시 실행 

<br>
<hr>

<br>
<br>

### < 연습 >

<br>

- `이벤트 정리` <br>

```javascript
useEffect(()=>{
    const handler = () => {
        console.log('window resized');
    }

    window.addEventListener('resize', handler);

    return () => {
        window.removeEventListener('resize', handler)
    }
}, [])
```

- 설명
```
이벤트 리스너를 처리할 때 
이 정리 메커니즘은 성능상의 이유로 중요

컴포넌트가 자주 마운트 및 마운트 해제되고 
마운트 해제 시 이벤트 리스너를 제거하지 않고 
마운트 시 이벤트 리스너를 등록하는 경우 
중복 이벤트 리스너가 여러 개 등록

이로 인해 메모리 누수 및 원치 않는 동작이 발생
```
