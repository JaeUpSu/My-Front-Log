<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `MyInfo Project`

<br>


* **정의**
* **기능**
* **컴포넌트**

<br>


> 정의

```
MyInfo 는 라우팅을 하지 않은 
Index 페이지만이 존재하기 때문에

react-scroll 라이브러리에 있는
Link 와 id 를 연결하여 해당 Part 로
Scroll 을 옮겨주는 기능
```
<br>
<br>

> 기능

```javascript
import { Link } from "react-scroll";

...

// to     ) Html element 요소 중 동일한 id 위치로 scroll 이동 

// spy    ) 특정 요소가 스크롤 위치에 도달했을 때, 
//          해당 요소를 감지하고 특정 동작을 수행 가능 기능

// smooth ) 부드럽게 스크롤을 이동하도록 해주는 옵션
<Link to="1" spy={true} smooth={true}>
    <span>Port-Folio</span>
</Link>

...

<div id="1">
    ...
</div>
```
<br>
<br>

> 컴포넌트

```javascript
import { Link } from "react-scroll";

export const Nav = () => {
    return (
        <div className="nav">
            <Link to="1" spy={true} smooth={true}>
                <span>It's Me</span>
            </Link>
            <Link to="2" spy={true} smooth={true}>
                <span>PortFolio</span>
            </Link>
            <Link to="3" spy={true} smooth={true}>
                <span>Linked In</span>
            </Link>
        </div>
    );
}
```
<br>
<br>

> hidden / show 를 적용한 컴포넌트

```javascript
export const topBtn = () => { 
 const [hidden, setHidden] = useState(true);

 useEffect(()=>{
    const handleShowTopBtn = () => {
        if (window.scrollY > 600) {
            setHidden(false);
        } else {
            setHidden(true);
        }
    }

    window.addEventListener("scroll", handleShowTopBtn);
    return () => {
        window.removeEventListener("scroll", handleShowTopBtn)
    }
 }, [])

 return !hidden && (
    <button id='top' onClick={scrollToTop}>Top</button>
 );
}
```
<br>

&nbsp;&nbsp;&nbsp; **`* scroll 이 600 이상이면 show 하고 `<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  `그 이하이면 hidden하게 만든 TopBtn`** 