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

Scroll 을 Top 으로 올리기 위해 만든 기능
```
<br>
<br>

> 기능

```javascript
const scrollToTop = () => {
    window.scrollTo({
        top: 0,
        behavior: 'smooth' // or auto
    })
}
//window.scroll(top, left, behavior);
//window.scrollTo({top, left, behavior})
//window.scrollTo(x_offset, y_offset) 
```
<br>
<br>

> 컴포넌트

```javascript
export const topBtn = () => 
    <button id='top' onClick={scrollToTop}>Top</button>
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