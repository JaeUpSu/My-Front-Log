<img src="../../Image/프로그래머스.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# 🔩 `택배 배달과 수거하기`

<br>


* **문제**
* **문제 예시**
* **풀이**
* **코드**

<br>

> 문제

```
cap 은 트럭에는 재활용 택배 상자를 최대 개수
n 은 집의 개수
deliveries[i] 는 i+1번째 집에 배달할 재활용 택배 상자의 개수
pickups[i] 는 i+1번째 집에서 수거할 빈 재활용 택배 상자의 개수

트럭 하나로 모든 배달과 수거를 마치고 
물류창고까지 돌아올 수 있는 
최소 이동 거리
```

<br>
<br>

> 문제 예시

```javascript
4	
5	
[1, 0, 3, 1, 2]	
[0, 3, 0, 4, 0]	
```

---

```
예시 결과 : 16
```


```javascript
2	
7	
[1, 0, 2, 0, 1, 0, 2]	
[0, 2, 0, 1, 0, 2, 0]
```

---

```
예시 결과 : 30
```


<br>
<br>

> 풀이

<br>

- 배달, 수거 최종 인덱스 정의

- 배달, 수거가 모두 완료될 때 까지 반복문
    
    - 배달 장소가 아니고 idx 가 0 이상이면 -1 반복문
    
    - 수거 장소가 아니고 idx 가 0 이상이면 -1 반복문
    
    - 트럭 수요 가능한 상자 개수 배달과 수거로 구분 정의
    
    - 배달과 수요 중 가능한 최댓값 idx 를 왕복 이동 거리에 더하기

    - 배달 cap 이 0보다 크고 배달 index 의 0 이상일 때 반복문 

        - 배달을 완료한 경우 -1 입력
        - 배달 트럭 수요 -1

        <br>

    - 수거 cap 이 0보다 크고 수거 index 의 0 이상일 때 반복문 

        - 수거를 완료한 경우 -1 입력
        - 수거 트럭 수요 -1

<br>
<br>

> 코드

```javascript
function solution(cap, n, deliveries, pickups) {
  let answer = 0;
  let [dIndex, pIndex] = [n - 1, n - 1];

  while (dIndex >= 0 || pIndex >= 0) {

    while (deliveries[dIndex] === 0 && dIndex >= 0) dIndex -= 1;
    while (pickups[pIndex] === 0 && pIndex >= 0) pIndex -= 1;
    
    let [dCap, pCap] = [cap, cap];
    answer += Math.max(dIndex + 1, pIndex + 1) * 2;
    
    while (dCap > 0 && dIndex >= 0) {
      if (deliveries[dIndex] > 0) {
        deliveries[dIndex] -= 1;
        dCap -= 1;
      } else {
        dIndex -= 1;
      }
    }

    while (pCap > 0 && pIndex >= 0) {
      if (pickups[pIndex] > 0) {
        pickups[pIndex] -= 1;
        pCap -= 1;
      } else {
        pIndex -= 1;
      }
    }

  }

  return answer;
}
```