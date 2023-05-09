<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `PortfolioSlider of MyInfo Project`

<br>

<img src="./Image/myinfo_3.png" style="object-fit: cover" width="650px" height="400px"/>


<br>

* **정의**
* **기능**
* **컴포넌트**
* **전체코드**
* **스타일**

<br>


> 정의

```
PortFolio 를 UI 적으로 보기 쉽게
Slider 로 만든 기능

메인 하나와 서브 두개로
총 세개의 컨텐츠가 한번에 보이며

back, next 버튼으로 
이전 혹은 다음 순서에 존재하는 
Contents 를 볼 수 있도록 구현
```
<br>
<br>

> 기능

<br>

&nbsp;&nbsp;`Modal Open`<br>
&nbsp;&nbsp; 상세한 포트폴리오를 보여주기 위한 모달 오픈 기능
```javascript
  const [modalIdx, setModalIdx] = useState(0); //modal창 노출 여부 결정
  const [modalOpen, setModalOpen] = useState(false); //modal창 노출 여부 결정

  const showModal = (e) => {
    const idx = Number(e.currentTarget.getAttribute("value"));
    if (feeds[order[idx]].ppts.length < 1) {
      alert("아직 업로드 되지 않았습니다!");
      return;
    }
    console.log(order[idx]);
    console.log(feeds[order[idx]].ppts);
    setModalIdx(order[idx]);
    setModalOpen(true); //클릭일때만 오픈
  };
```

<br>

&nbsp;&nbsp;`onBack or onNext`<br>
&nbsp;&nbsp; Slider 의 버튼 이벤트<br>
&nbsp;&nbsp; 이벤트 후 Feed 리스트의 재배치
```javascript
  const [isNext, setIsNext] = useState(false);
  const [current, setCurrent] = useState(0);
  const [order, setOrder] = useState([1, 2, 3]);

  // 이전 값이 존재하면 동작하도록 구현
  const onBack = () => {
    if (order[0] > 0) {
      setIsNext(false);
      setCurrent((current) => current - 1);
    }
  };
  
  // 다음 값이 존재하면 동작하도록 구현
  const onNext = () => {
    if (order[2] < feeds.length - 1) {
      setIsNext(true);
      setCurrent((current) => current + 1);
    }
  };
  
  // Contents Index 변화에 따른 재배치
  useEffect(() => {
    let reOrder = [];
    order.forEach((item) => {
      let itemValue = item;
      if (isNext) {
        itemValue += 1;
      } else {
        itemValue -= 1;
      }
      reOrder.push(itemValue);
    });
    setOrder(reOrder);
  }, [current]);

```


<br>
<br>

> 컴포넌트

```javascript
<div id="2" className={styles.portfolio}>
      <h1 className={styles.portfolio_label}>Port-Folio</h1>
      <div class="support-grid"></div>

      <div className={styles.band}>
        <div className={styles.item_1}>
          <a className={styles.card}>
            <div
              className={styles.card_thumb}
              style={{
                backgroundImage: `url(${feeds[order[0]]?.img})`,
              }}
            ></div>
            <article className={styles.card_article}>
              <div>
                <TitleBox>
                  <h1 className={styles.card_title}>
                    {feeds[order[0]]?.subtitle}
                  </h1>{" "}
                  <br /> <Title>{feeds[order[0]]?.title}</Title>
                </TitleBox>
                <br /> <br />
                <p className={styles.card_text}>{feeds[order[0]]?.contents}</p>
              </div>
              <div>
                <Btn onClick={showModal} value={0}>
                  Detail
                </Btn>
                {modalOpen && modalIdx == order[0] && (
                  <FeedModal
                    setModalOpen={setModalOpen}
                    ppts={feeds[modalIdx]?.ppts}
                  />
                )}
                <span className={styles.card_cat}>{feeds[order[0]]?.info}</span>
              </div>{" "}
            </article>
          </a>
        </div>
        <div class="item-2">
          <a className={styles.card}>
            <div
              className={styles.card_thumb}
              style={{
                backgroundImage: `url(${feeds[order[1]]?.img})`,
              }}
            ></div>
            <article className={styles.card_article}>
              <TitleBox>
                <h1 className={styles.card_title}>
                  {feeds[order[1]]?.subtitle}
                </h1>{" "}
                <br /> <Title>{feeds[order[1]]?.title}</Title>
              </TitleBox>
              <br /> <br />
              <p className={styles.card_text}>{feeds[order[1]]?.contents}</p>
              <div>
                <Btn onClick={showModal} value={1}>
                  Detail
                </Btn>
                {modalOpen && modalIdx == order[1] && (
                  <FeedModal
                    setModalOpen={setModalOpen}
                    ppts={feeds[modalIdx]?.ppts}
                  />
                )}
                <span className={styles.card_cat}>{feeds[order[1]]?.info}</span>
              </div>
            </article>
          </a>
        </div>

        <div class="item-3">
          <a className={styles.card}>
            <div
              className={styles.card_thumb}
              style={{
                backgroundImage: `url(${feeds[order[2]]?.img})`,
              }}
            ></div>
            <article className={styles.card_article}>
              <TitleBox>
                <h1 className={styles.card_title}>
                  {feeds[order[2]]?.subtitle}
                </h1>
                <br /> <Title>{feeds[order[2]]?.title}</Title>
              </TitleBox>
              <br /> <br />
              <p className={styles.card_text}>{feeds[order[2]]?.contents}</p>
              <div>
                <Btn onClick={showModal} value={2}>
                  Detail
                </Btn>
                {modalOpen && modalIdx == order[2] && (
                  <FeedModal
                    setModalOpen={setModalOpen}
                    ppts={feeds[modalIdx]?.ppts}
                  />
                )}
                <span className={styles.card_cat}>{feeds[order[2]]?.info}</span>
              </div>
            </article>
          </a>
        </div>
      </div>
      <SliderBtn
        class="back-btn"
        style={{ left: "10px", color: "rgb(56 56 56)" }}
        onClick={onBack}
      >
        <FontAwesomeIcon size="2x" icon={Solid.faLessThan} />
      </SliderBtn>
      <SliderBtn
        class="next-btn"
        style={{ right: "10px", color: "rgb(56 56 56)" }}
        onClick={onNext}
      >
        <FontAwesomeIcon size="2x" icon={Solid.faGreaterThan} />
      </SliderBtn>
    </div>
```
<br>
<br>

> 전체 코드

```javascript
import styles from "./portfolio.module.css";
import styled from "styled-components";

import FeedModal from "../modal/feed_modal";
import { useEffect, useState } from "react";
import { FontAwesomeIcon } from "@fortawesome/react-fontawesome";
import * as Solid from "@fortawesome/free-solid-svg-icons";
import axios from "axios";

const Btn = styled.button`
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;

  width: 180px;
  height: 46px;

  background: #1552f0;
  border: none;
  border-radius: 6px;
  cursor: pointer;

  font-weight: 700;
  font-size: 18px;
  color: white;

  margin: 30px 0px;
  position: relative;
  top: 0px;

  &:hover {
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);

    background: #1332a0;
    top: -1px;
  }
`;

const SliderBtn = styled.div`
  position: absolute;
  top: 54.5%;
  transform: translateY(-50%);
  width: 40px;
  height: 730px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  color: #fff;
  font-size: 25px;
  transition: all 300ms ease-in-out;
  &:hover {
    background: rgba(0, 0, 0, 0.1);
  }
`;

const TitleBox = styled.div`
  display: flex;
  flex-direction: column;
  align-items: space-around;
`;
const Title = styled.strong`
  margin-top: 10px;
  font-size: 30px;
`;

function PortFolio() {
  const [isNext, setIsNext] = useState(false);
  const [current, setCurrent] = useState(0);
  const [order, setOrder] = useState([1, 2, 3]);
  const [feeds, setFeeds] = useState([]);
  const [modalIdx, setModalIdx] = useState(0); //modal창 노출 여부 결정
  const [modalOpen, setModalOpen] = useState(false); //modal창 노출 여부 결정

  const showModal = (e) => {
    const idx = Number(e.currentTarget.getAttribute("value"));
    if (feeds[order[idx]].ppts.length < 1) {
      alert("아직 업로드 되지 않았습니다!");
      return;
    }
    setModalIdx(order[idx]);
    setModalOpen(true); //클릭일때만 오픈
  };

  const onBack = () => {
    if (order[0] > 0) {
      setIsNext(false);
      setCurrent((current) => current - 1);
    }
  };
  const onNext = () => {
    if (order[2] < feeds.length - 1) {
      setIsNext(true);
      setCurrent((current) => current + 1);
    }
  };

  useEffect(() => {
    let reOrder = [];
    order.forEach((item) => {
      let itemValue = item;
      if (isNext) {
        itemValue += 1;
      } else {
        itemValue -= 1;
      }
      reOrder.push(itemValue);
    });
    setOrder(reOrder);
  }, [current]);

  useEffect(() => {
    axios
      .get("http://127.0.0.1:8000/api/v1/feeds/")
      .then((response) => {
        setFeeds([...response.data]);
      })
  }, []);

  return (
    <div id="2" className={styles.portfolio}>
      <h1 className={styles.portfolio_label}>Port-Folio</h1>
      <div class="support-grid"></div>

      <div className={styles.band}>
        <div className={styles.item_1}>
          <a className={styles.card}>
            <div
              className={styles.card_thumb}
              style={{
                backgroundImage: `url(${feeds[order[0]]?.img})`,
              }}
            ></div>
            <article className={styles.card_article}>
              <div>
                <TitleBox>
                  <h1 className={styles.card_title}>
                    {feeds[order[0]]?.subtitle}
                  </h1>{" "}
                  <br /> <Title>{feeds[order[0]]?.title}</Title>
                </TitleBox>
                <br /> <br />
                <p className={styles.card_text}>{feeds[order[0]]?.contents}</p>
              </div>
              <div>
                <Btn onClick={showModal} value={0}>
                  Detail
                </Btn>
                {modalOpen && modalIdx == order[0] && (
                  <FeedModal
                    setModalOpen={setModalOpen}
                    ppts={feeds[modalIdx]?.ppts}
                  />
                )}
                <span className={styles.card_cat}>{feeds[order[0]]?.info}</span>
              </div>{" "}
            </article>
          </a>
        </div>
        <div class="item-2">
          <a className={styles.card}>
            <div
              className={styles.card_thumb}
              style={{
                backgroundImage: `url(${feeds[order[1]]?.img})`,
              }}
            ></div>
            <article className={styles.card_article}>
              <TitleBox>
                <h1 className={styles.card_title}>
                  {feeds[order[1]]?.subtitle}
                </h1>{" "}
                <br /> <Title>{feeds[order[1]]?.title}</Title>
              </TitleBox>
              <br /> <br />
              <p className={styles.card_text}>{feeds[order[1]]?.contents}</p>
              <div>
                <Btn onClick={showModal} value={1}>
                  Detail
                </Btn>
                {modalOpen && modalIdx == order[1] && (
                  <FeedModal
                    setModalOpen={setModalOpen}
                    ppts={feeds[modalIdx]?.ppts}
                  />
                )}
                <span className={styles.card_cat}>{feeds[order[1]]?.info}</span>
              </div>
            </article>
          </a>
        </div>

        <div class="item-3">
          <a className={styles.card}>
            <div
              className={styles.card_thumb}
              style={{
                backgroundImage: `url(${feeds[order[2]]?.img})`,
              }}
            ></div>
            <article className={styles.card_article}>
              <TitleBox>
                <h1 className={styles.card_title}>
                  {feeds[order[2]]?.subtitle}
                </h1>
                <br /> <Title>{feeds[order[2]]?.title}</Title>
              </TitleBox>
              <br /> <br />
              <p className={styles.card_text}>{feeds[order[2]]?.contents}</p>
              <div>
                <Btn onClick={showModal} value={2}>
                  Detail
                </Btn>
                {modalOpen && modalIdx == order[2] && (
                  <FeedModal
                    setModalOpen={setModalOpen}
                    ppts={feeds[modalIdx]?.ppts}
                  />
                )}
                <span className={styles.card_cat}>{feeds[order[2]]?.info}</span>
              </div>
            </article>
          </a>
        </div>
      </div>
      <SliderBtn
        class="back-btn"
        style={{ left: "10px", color: "rgb(56 56 56)" }}
        onClick={onBack}
      >
        <FontAwesomeIcon size="2x" icon={Solid.faLessThan} />
      </SliderBtn>
      <SliderBtn
        class="next-btn"
        style={{ right: "10px", color: "rgb(56 56 56)" }}
        onClick={onNext}
      >
        <FontAwesomeIcon size="2x" icon={Solid.faGreaterThan} />
      </SliderBtn>
    </div>
  );
}

export default PortFolio;

```
<br>


> 스타일

```css
@import url("https://fonts.googleapis.com/css2?family=Paytone+One&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Black+Han+Sans&display=swap");

.portfolio {
  background-color: #e4f2ff;
  padding-bottom: 100px;
  padding-top: 5px;
  text-align: center;
  border-top: 1px solid lightgray;
  border-bottom: 1px solid lightgray;
  position: relative;
}

.portfolio:hover {
  color: black;
}

.portfolio_label {
  font-family: "Paytone One", sans-serif;
  font-size: 38px;
  font-weight: 200;
  text-align: center;
  margin: 90px 0 50px 0;
  color: #000000;
}

/* ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ */

.band {
  width: 90%;
  max-width: 1240px;
  margin: 0 auto;

  display: grid;

  grid-template-columns: 1fr;
  grid-template-rows: auto;
  grid-gap: 20px;
}

@media only screen and (min-width: 500px) {
  .band {
    grid-template-columns: 1fr 1fr;
  }
  .item_1 {
    grid-column: 1 / span 2;
  }
  .item_1 h1 {
    font-size: 30px;
  }
}

@media only screen and (min-width: 850px) {
  .band {
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }
}

/* card */

.card {
  min-height: 100%;
  background: white;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  text-decoration: none;
  color: #444;
  position: relative;
  top: 0;
  transition: all 0.1s ease-in;
  height: 770px;
}

.card:hover {
  top: -2px;
  color: #444;
  box-shadow: 0 8px 10px rgba(0, 0, 0, 0.2);
}

.card_article {
  padding: 20px;
  display: flex;

  flex: 1;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}
strong {
  margin-top: 30px;
}
.card_thumb {
  padding-bottom: 60%;
  background-size: cover;
  object-fit: cover;
  background-position: center center;
}

.card_text {
  flex: 1;
  line-height: 1.4;
  margin: 0;
}

.card_title {
  font-size: 20px;
  margin: 0;
  color: #333;
}

.card_cat {
  font-size: 12px;
  font-weight: bold;
  color: #999;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin: 2em 0 0 0;
}

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