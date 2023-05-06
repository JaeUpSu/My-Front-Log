<img src="../Image/es6_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Promises 알아보자`

<br>

* **정의**
* **사용법**
* **사용 이유**
* **예시 코드**

<br>
<br>

> 정의 

```
비동기 작업을 처리하고 
이를 좀 더 구조화하고 다루기 쉽게 만드는 객체

작업의 상태를 나타내는 세 가지 상태를 가지며
비동기 작업의 성공 또는 실패와 관련된 
결과를 나타내는 용도로 사용
```
<br>
<br>

> 사용법


```
const promise = new Promise((resolve, reject) => {
  
  // 비동기 작업 수행
  if (/* 작업 성공 */) {

    // 성공 결과 처리
    resolve(result); 

  } else {

    // 실패 결과 처리
    reject(error); 

  }
});

promise.then((result) => {
  // 성공적으로 작업이 완료된 경우 처리
}).catch((error) => {
  // 작업 실패한 경우 처리
});
```
<br>
<br>

> 사용이유

```
* 비동기 작업의 구조화

* 에러 처리 (catch, finally)

* 비동기 작업의 결과 전달
```
<br>
<br>

> 예시 코드

```
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = { name: "John", age: 30 };
      if (data) {
        resolve(data); // 성공적으로 작업 완료됨
      } else {
        reject("Error fetching data"); // 작업 실패
      }
    }, 2000);
  });
}

fetchData()
  .then((data) => {
    console.log("Data:", data);
  })
  .catch((error) => {
    console.log("Error:", error);
  });
```

