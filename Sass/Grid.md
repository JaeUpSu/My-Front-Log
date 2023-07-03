<img src="../Image/sass.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Grid 알아보자`

<br>

* **정의**
* **컨테이너**
* **아이템**

<br>

> 정의

```
CSS에서 사용할 수 있는 강력한 레이아웃 시스템

주로 2차원 그리드 시스템(예: 행과 열을 따라)에서 요소를 정렬하도록 설계
```
<br>


> 컨테이너

- `display`
```
디스플레이 속성을 grid 또는 
inline-grid로 설정하여 
HTML 요소를 그리드 컨테이너로 전환
```
- `grid-template-columns, grid-template-rows`
```
이러한 속성은 그리드의 열과 행의 수와 크기를 정의합니다. 크기를 고정(예: ​​px), 유연(예: fr 단위) 또는 혼합으로 지정 가능
```
- `grid-template-areas`
```
이 속성은 grid-area 속성으로 지정된 그리드 영역의 이름을 참조하여 그리드 템플릿을 정의
```
- `grid-template`
```
grid-template-rows, grid-template-columns 및 grid-template-areas의 속기 속성
```
- `grid-column-gap, grid-row-gap`
```
이러한 속성은 열/행 사이의 간격 크기를 정의
```
- `grid-gap`
```
grid-row-gap 및 grid-column-gap의 속기 속성
```
- `grid-auto-columns, grid-auto-rows`
```
이러한 속성은 그리드 레이아웃에서 자동으로 생성되는 열/행의 크기를 정의
```
- `grid-auto-flow`
```
이 속성은 자동 배치 항목이 그리드에 삽입되는 방식을 정의
```
- `grid`
```
위에서 언급한 모든 그리드 속성에 대한 속기 속성
```
<br>


> 아이템

- `grid-column-start, grid-column-end, grid-row-start, grid-row-end`
```
이러한 속성은 항목이 시작하고 끝나는 위치를 정의합니다. 이러한 속성을 선으로 채우기 가능, 숫자 값.
```
- `grid-column, grid-row`
```
grid-column-start/grid-column-end 및 grid-row-start/grid-row-end의 약식 속성, 각기.
```
- `grid-area`
```
이 속성은 그리드 항목의 이름을 지정하는 데 사용되며 'grid-template-areas' 속성에서 참조 가능
```
- `justify-self`
```
이 속성은 행(인라인) 축을 따라 그리드 항목을 정렬하는 데 사용
```
- `align-self`
```
이 속성은 열(블록) 축을 따라 그리드 항목을 정렬하는 데 사용
```
- `place-self`
```
align-self 및 justify-self를 모두 설정하는 속기 속성
```
<br>
