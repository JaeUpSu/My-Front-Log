<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `RangeSlider of Bangsam Project`

<br>


* **설명**
* **기능**
* **컴포넌트**
* **개선점**

<br>


> 설명

```
Chakra UI 를 통해 구현한 
Slider 로 실시간으로 가격을 표현

단방향 바인딩에 어긋난 상태 저장
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp;`state`<br>
 &nbsp;&nbsp;&nbsp; session 에 저장된 상태값을 기본값으로 설정
```javascript
  const [values, setValues] = useState(
    sessionStorage.getItem(names.eng)
      ? sessionStorage.getItem(names.eng).split(",")
      : [0, 30]
  );
```
<br>

## &nbsp;&nbsp;`onUpdate`<br>
 &nbsp;&nbsp;&nbsp; fetch 를 확인하면 상위 컴포넌트의 상태 값을 갱신
```javascript
  useEffect(() => {
    onUpdate((prices) => {
      const newPrices = prices.map((price, _idx) => {
        if (_idx == idx) {
          const newPrice = getPrices(range);
          return newPrice;
        } else {
          return price;
        }
      });
      return newPrices;
    });
  }, [isFetch]);
```
<br>

## &nbsp;&nbsp;`setRange`<br>
 &nbsp;&nbsp;&nbsp; 숫자를 입력값으로 가격을 만, 억 등으로 표현
```javascript
  useEffect(() => {
    sessionStorage.setItem(names.eng, values);
    setRange(getPriceRange(values, options[names.eng].steps));
  }, [values]);
```
<br>
<br>

> 컴포넌트

<br>

 &nbsp;&nbsp; &nbsp;`RangeSlider.jsx`
```javascript
import { useEffect, useRef, useState } from "react";
import { options } from "../../services/data";
import { getPriceRange } from "../../utils/getPriceRange";

import {
  RangeSlider,
  RangeSliderTrack,
  RangeSliderFilledTrack,
  RangeSliderThumb,
  RangeSliderMark,
  Text,
  Box,
  Highlight,
  Flex,
  HStack,
  Button,
} from "@chakra-ui/react";
import { getPrices } from "../../utils/getPrices";

function OptionRangeSlider({ idx, names, onUpdate }) {
  const [values, setValues] = useState(
    sessionStorage.getItem(names.eng)
      ? sessionStorage.getItem(names.eng).split(",")
      : [0, 30]
  );
  const [range, setRange] = useState("");
  const [isFetch, setFetch] = useState(false);

  const labels = options[names.eng].labels;

  const handleChange = (newValues) => {
    setValues(newValues);
  };

  const handleFetch = () => {
    setFetch(!isFetch);
  };

  useEffect(() => {
    sessionStorage.setItem(names.eng, values);
    setRange(getPriceRange(values, options[names.eng].steps));
  }, [values]);

  useEffect(() => {
    onUpdate((prices) => {
      const newPrices = prices.map((price, _idx) => {
        if (_idx == idx) {
          const newPrice = getPrices(range);
          return newPrice;
        } else {
          return price;
        }
      });
      return newPrices;
    });
  }, [isFetch]);

  return (
    <Box mr="2vw" my="2vh">
      <HStack justifyContent="space-between" w="100%">
        <Text fontWeight="bold" fontSize="17px">
          {names.kor}
          <Highlight
            query={range}
            styles={
              names.kor.length < 3
                ? {
                    ml: "36px",
                    px: "3",
                    py: "2",
                    rounded: "full",
                    color: "gray",
                    fontSize: "15px",
                  }
                : {
                    ml: "20px",
                    px: "3",
                    py: "2",
                    rounded: "full",
                    color: "gray",
                    fontSize: "15px",
                  }
            }
          >
            {range}
          </Highlight>
        </Text>
        <Button colorScheme="red" size="sm" onClick={handleFetch}>
          Search
        </Button>
      </HStack>
      <RangeSlider
        mt="20px"
        mb="20px"
        mx="10px"
        defaultValue={values[0] ? values : [0, 30]}
        min={0}
        max={30}
        step={1}
        w="450px"
        onChange={handleChange}
      >
        {labels.map((item, idx) => {
          return (
            <RangeSliderMark key={idx} value={idx * 10} mt="16px" w="100%">
              {item}
            </RangeSliderMark>
          );
        })}
        <RangeSliderTrack bg="red.100" ml="10px">
          <RangeSliderFilledTrack bg="red.200" w="100%" />
        </RangeSliderTrack>
        <RangeSliderThumb
          max={values[0] ? values[0] - 10 : -10}
          value={values[0] ? values[0] : 0}
          boxSize={5}
          index={0}
          bg="red.400"
          mr={`20px`}
        />
        <RangeSliderThumb
          min={values[0] ? values[1] + 10 : 10}
          value={values[0] ? values[1] : 30}
          boxSize={5}
          index={1}
          bg="red.400"
          ml={`20px`}
        />
      </RangeSlider>
    </Box>
  );
}
export default OptionRangeSlider;
```


<br>
<br>


> 개선점

```
Recoil 을 사용한 상태 변화

Slider 의 범위로 바뀌는 가격을 보여주는 
Text 가 완벽하게 적용
```