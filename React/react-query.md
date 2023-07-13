<img src="../Image/react_js_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `React-Query 를 알아보자`

<br>


* **정의**
* **기능**
* **코드**

<br>

> 정의

``` 
즉시 사용 가능한 캐싱 및 기타 기능을 제공

React 생태계에서 널리 사용되는 
데이터 가져오기 라이브러리
```

<br>
<br>

> 기능

<br>

- `자동 캐싱 및 동기화`
- `데이터 가져오기`
- `Devtools`
- `페이지 매김 및 무한 쿼리`
- `병렬 및 종속 쿼리`

<br>

```
React용 데이터 동기화 라이브러리
React 애플리케이션에서 서버 상태를 
가져오고, 캐시하고, 업데이트 가능
```
<br>
<br>



> 코드

<br>

- `기본사용법`

&nbsp;&nbsp;&nbsp; todos 는 캐시의 고유키 <br>
&nbsp;&nbsp;&nbsp; fetchTodoList 는 데이터 가져오는 비동기 함수
```javascript
import { useQuery } from 'react-query'

function MyComponent() {
  const { isLoading, error, data } = useQuery('todos', fetchTodoList)

  // rest of your component
}
```

<br>

- `데이터 미리 가져오기`

&nbsp;&nbsp;&nbsp; 사전에 데이터를 가져와서  <br>
&nbsp;&nbsp;&nbsp; 캐시에 저장하는 prefetchQuery 기능을 제공
```javascript
import { prefetchQuery } from 'react-query'

prefetchQuery('todos', fetchTodoList)
```

<br>

- `돌연변이 및 캐시 업데이트`

&nbsp;&nbsp;&nbsp;  POST, PUT, DELETE 요청에  <br>
&nbsp;&nbsp;&nbsp; 사용할 수 있는 useMutation 후크도 제공
```javascript
import { useMutation, useQueryClient } from 'react-query'

function MyComponent() {
  const queryClient = useQueryClient()

  const mutation = useMutation(newTodo => createTodo(newTodo), {
    onSuccess: () => {
      queryClient.invalidateQueries('todos')
    }
  })

  // rest of your component
}
```

<br>

- `오래된 데이터 및 배경 업데이트`

&nbsp;&nbsp;&nbsp; 부실 데이터(캐시에 있지만 만료된 데이터)를 사용하여 <br>
&nbsp;&nbsp;&nbsp; 사용자에게 즉시 무언가를 표시할 수 있으며<br>
&nbsp;&nbsp;&nbsp; 업데이트된 데이터를 가져오기 위해<br>
&nbsp;&nbsp;&nbsp; 백그라운드에서 가져오기가 수행 
```javascript
const { data } = useQuery('todos', fetchTodoList, {
  staleTime: 1000 * 60 * 5, // data becomes stale after 5 minutes
  cacheTime: 1000 * 60 * 30, // data is removed from cache after 30 minutes
})
```