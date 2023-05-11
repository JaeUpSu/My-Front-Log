<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `RadioCard of Bangsam Project`

<br>


* **설명**
* **기능**
* **컴포넌트**

<br>


> 설명

```
Chakra UI 를 통해 구현한 
Data List 를 선택할 수 있게 만든 모달

이전 필요 상태의 존재 여부에 따라 활성화

단방향 바인딩에 어긋난 상태 저장
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp;`onSelect`
```javascript
const onSelect = (e) => {
    const selectedVal = e.currentTarget.getAttribute("value");
    const selectedIdx = e.currentTarget.getAttribute("idx");
    setBtnName(selectedVal);
    onNextActive();
    sessionStorage.setItem(name, selectedVal);
    sessionStorage.setItem(name + "Idx", selectedIdx);

    if (name.includes("gugunsi")) {
      sessionStorage.setItem("ebmyeondong", "nothing");
    }

    onSetAddress((items) => {
      let nextAddress = [0, 0, 0];
      items.forEach((item, idx) => {
        if (name == addressKinds[idx]) {
          nextAddress[idx] = selectedVal;
        } else {
          nextAddress[idx] = item;
        }
      });
      return nextAddress;
    });
    onClose();
  };
```
<br>
<br>

> 컴포넌트

<br>

 &nbsp;&nbsp; &nbsp;`SelectModal.jsx`
```javascript
import { useState } from "react";
import { Flex, Box, useRadio, useRadioGroup } from "@chakra-ui/react";

import { optionsMenu } from "../../services/data";

function RadioCard({ name, radio, onSelect }) {
  const { getInputProps, getCheckboxProps } = useRadio(radio);
  const [checked, setChecked] = useState(false);

  const input = getInputProps();
  const checkbox = getCheckboxProps();

  const onRadio = () => {
    const value = sessionStorage.getItem(name);
    const idx = optionsMenu.findIndex((val) => val.eng === name);

    sessionStorage.setItem(name, input.value);
    if (input.value != value) {
      setChecked(!checked);
    }

    onSelect((opts) => {
      const newOpts = opts.map((item, i) => {
        if (idx != i) {
          return item;
        } else {
          return input.value;
        }
      });
      return newOpts;
    });
  };

  return (
    <Box as="label" m="5px">
      <input {...input} />
      <Flex
        {...checkbox}
        backgroundColor="rgb(233,239,244)"
        cursor="pointer"
        fontWeight="600"
        borderRadius="md"
        _checked={{
          bg: "red.300",
          color: "white",
        }}
        px={3}
        py={2}
        w="32"
        onClick={onRadio}
        justifyContent="center"
        position="relative"
      >
        <Box
          {...checkbox}
          opacity="0"
          position="absolute"
          left="10px"
          _checked={{
            opacity: "1",
          }}
          _focus={{ opacity: "1" }}
        ></Box>
        {radio.value}
      </Flex>
    </Box>
  );
}
function DataRadioCard({ name, valueName, data, defaultData, onUpdate }) {
  const { getRootProps, getRadioProps } = useRadioGroup({
    name: `${name}`,
    defaultValue: `${
      sessionStorage.getItem(valueName)
        ? sessionStorage.getItem(valueName)
        : defaultData
    }`,
  });

  const group = getRootProps();

  return (
    <Flex>
      <Flex
        {...group}
        flexWrap="wrap"
        alignItems={"center"}
        justifyContent="flex-start"
        w={valueName === "sellKind" ? "580px" : "32vw"}
      >
        {data.map((value) => {
          const radio = getRadioProps({ value });
          return (
            <RadioCard
              key={value}
              name={valueName}
              radio={radio}
              onSelect={onUpdate}
            >
              {value}
            </RadioCard>
          );
        })}
      </Flex>
    </Flex>
  );
}

export default DataRadioCard;
```

