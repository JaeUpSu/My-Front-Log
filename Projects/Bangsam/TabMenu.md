<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `탭 메뉴 of Bangsam Project`

<br>


* **설명**
* **기능**
* **컴포넌트**

<br>


> 설명

```
Chakra UI 를 통해 구현한 
Tab Menu

중첩 라우팅
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp;`tab navigate`<br>
 &nbsp;&nbsp;&nbsp; tab 선택 시 navigate 설정
```javascript
  const tabMap = {
    "": 0,
    sell: 1,
    notsell: 2,
  };
  const selectedTabIndex = tabMap[pathname.split("/").slice(-1)[0]];
  const changeTab = (index) => {
    navigate(`./${Object.keys(tabMap)[index]}`);
  };
```
<br>

## &nbsp;&nbsp;`중첩라우팅의 Outlet`<br>
 &nbsp;&nbsp;&nbsp; outlet 을 통한 children 라우팅
```javascript
  ...
<TabPanel p="2px">
   <Outlet />
</TabPanel>
```
<br>
<br>

> 컴포넌트

<br>

 &nbsp;&nbsp; &nbsp;`SellHistory.jsx`
```javascript
import React from "react";
import {
  Tabs,
  TabList,
  TabPanels,
  Tab,
  TabPanel,
  HStack,
  Flex,
} from "@chakra-ui/react";
import { Outlet, useLocation, useNavigate } from "react-router-dom";
import useUser from "../../hooks/useUser";
import Helmet from "react-helmet";

export default function SellHistory() {
  const { user } = useUser();
  const { pathname } = useLocation();
  const navigate = useNavigate();
  const tabMap = {
    "": 0,
    sell: 1,
    notsell: 2,
  };
  const selectedTabIndex = tabMap[pathname.split("/").slice(-1)[0]];
  const changeTab = (index) => {
    navigate(`./${Object.keys(tabMap)[index]}`);
  };

  return (
    <Tabs
      isLazy
      isFitted
      variant="unstyled"
      onChange={changeTab}
      defaultIndex={selectedTabIndex}
    >
      <Helmet>
        <title>{`판매내역 ${user?.name} - BANGSAM`}</title>
      </Helmet>
      <HStack alignItems="flex-start">
        <Flex
          h="74vh"
          w="15vw"
          backgroundColor="rgb(233,239,244,0.5)"
          borderRadius="md"
          alignItems="flex-start"
          justifyContent="center"
          p="1"
        >
          <TabList
            mt="3vh"
            w="9vw"
            h="20vh"
            minW="55px"
            flexDirection="column"
            borderTopRadius={"3xl"}
            justifyContent="space-between"
          >
            <Tab
              borderColor="white"
              borderRadius="7px"
              fontSize={{
                sm: "xs",
                md: "sm",
                lg: "md",
              }}
              bg={"gray.200"}
              _selected={{ color: "white", bg: "#ff535e" }}
            >
              전체
            </Tab>
            <Tab
              borderColor="white"
              borderRadius="7px"
              fontSize={{
                sm: "xs",
                md: "sm",
                lg: "md",
              }}
              mt="2vh"
              bg={"gray.200"}
              _selected={{ color: "white", bg: "#ff535e" }}
            >
              판매중
            </Tab>
            <Tab
              borderColor="white"
              borderRadius="7px"
              fontSize={{
                sm: "xs",
                md: "sm",
                lg: "md",
              }}
              mt="2vh"
              bg={"gray.200"}
              _selected={{ color: "white", bg: "#ff535e" }}
            >
              판매완료
            </Tab>
          </TabList>
        </Flex>
        <TabPanels>
          <TabPanel p="2px">
            <Outlet />
          </TabPanel>
          <TabPanel p="2px">
            <Outlet />
          </TabPanel>
          <TabPanel p="2px">
            <Outlet />
          </TabPanel>
        </TabPanels>
      </HStack>
    </Tabs>
  );
}
```