# ⭐ Github &nbsp; - 마크다운

<br/>

## &nbsp; 📰 설명

<br/>

> `Markdown`은 사용자가 간단한 구문으로 `텍스트 서식을 지정하고 스타일을 지정할 수 있는 경량 마크업 언어` > <br/> > <br/>
> 2004년 John Gruber가 사람들이 일반 텍스트로 작성할 수 있으면서도 구조화되고 시각적으로 매력적인 문서를 생성할 수 있도록 하는 것을 목표로 구현
> <br/>

<br/>

    "특수 문자와 구문을 사용"

    제목, 볼드체 및 이탤릭체 텍스트, 목록, 링크, 이미지, 코드 블록과 같은 서식을 나타냄

    예를 들어 줄 시작 부분에 단일 해시(#)를 사용하면 제목이 생성되고 별표(\*)를 사용하면 목록에 글머리 기호가 생성

<br/>

다양한 도구를 사용하여 HTML 또는 기타 형식으로 쉽게 변환 가능
<br/><br/>
문서 작성, 블로그 게시물 작성 및 기술 프로젝트 공동 작업에 널리 사용
<br/><br/>
GitHub, Stack Overflow 및 Slack을 비롯한 많은 플랫폼과 애플리케이션에서 광범위하게 지원

<br/>
<br/>

## &nbsp; ➕ 장점

<br/>

> 배우기 쉬움

&nbsp; &nbsp;사전 프로그래밍 경험 없이도 누구나 쉽게 학습 가능

<br/>

> 플랫폼 독립적

&nbsp; &nbsp;Windows, Mac 및 Linux를 포함한 <br/>&nbsp; &nbsp;모든 플랫폼과 모든 웹 브라우저에서 사용 가능

<br/>

> 이식성

&nbsp; &nbsp;특별한 소프트웨어나 플러그인 없이도 <br/>&nbsp; &nbsp;모든 장치에서 쉽게 공유하고 열 수 있는 일반 텍스트 파일

<br/>

> 깨끗하고 단순함

&nbsp; &nbsp;깨끗하고 눈에 잘 띄지 않도록 설계되어 콘텐츠에 집중 가능

<br/>

> 다양한 출력 형식 지원

&nbsp; &nbsp;HTML, PDF 및 Microsoft Word를 포함한 <br/>&nbsp; &nbsp;다양한 출력 형식으로 변환 가능
<br/>
<br/>

## &nbsp; ➖ 단점

<br/>

> 제한된 서식 옵션

&nbsp; &nbsp;굵게, 기울임꼴, 제목 및 목록과 같은 기본 서식 옵션으로 <br/>&nbsp; &nbsp;제한 보다 복잡한 서식에는 추가 도구가 필요

<br/>

> 표준화 없음

&nbsp; &nbsp;표준화된 버전이 존재 X<br/>&nbsp; &nbsp;즉, 구현마다 구문이 약간 차이 존재

<br/>

> WYSIWYG 편집 없음

&nbsp; &nbsp;일반적으로 일반 텍스트로 편집되므로 <br/>&nbsp; &nbsp;일부 사용자는 최종 출력을 시각화하기 어려움

<br/>

> 변환 표준화 부족

&nbsp; &nbsp;다른 형식으로의 변환은 표준화되지 않았으며 <br/>&nbsp; &nbsp;때로는 동일한 도구를 사용해도 다른 결과가 발생 가능

<br>
<br>
<br>
<br>

---

<br>
<br>

## &nbsp; 🦴 사용방법

<br>
<br>


# #  `H1~H6 글머리 (#)`

    # This is a H1
    ## This is a H2
    ### This is a H3
    #### This is a H4
    ##### This is a H5
    ###### This is a H6

# This is a H1

## This is a H2

### This is a H3

#### This is a H4

##### This is a H5

###### This is a H6
<br>

<br>

# #  `큰 제목 & 작은 제목 (=, -)`

    큰 제목
    =
    작은 제목
    -


큰 제목
=
작은 제목
-
<br>

<br>

# #  `블럭 인용 문자 (>)`

    > 블럭 인용 문자입니다 1
    >	> 블럭 인용 문자입니다 2
    >	>	> 블럭 인용 문자입니다 3

> 블럭 인용 문자입니다 1
>	> 블럭 인용 문자입니다 2
>	>	> 블럭 인용 문자입니다 3
    
<br>
<br>


# #  `순서 리스트 (1,2,3,...)`

    1. 첫
    3. 서이
    2. 둘

1. 첫
3. 서이
2. 둘

### => 입력한 숫자의 순서대로 배치
    
<br>
<br>


# #  `순서 없는 리스트 (*,+,-)`

    * First
        * Second
            * Third

    + First
        + Second
            + Third
    
    - First
        - Second
            - Third

* First
    * Second
        * Third

+ First
    + Second
        + Third
    
- First
    - Second
        - Third
    
<br>
<br>


# #  `띄어쓰기 (nbsp === ' ')`

    &nbsp;&nbsp;&nbsp;띄어쓰기

|&nbsp;&nbsp;&nbsp;띄어쓰기
    
<br>
<br>


# #  `들여쓰기 (4 x ' ' Or 1 x tab)`

    들여쓰기 입니다
        4 x ' ' 입니다
        1 x tab 입니다

<br>
<br>


# #  `코드 (<pre><code> And ```)`


-   <br/> `<pre>`<br/>
    `<code>`<br/>
    &nbsp; &nbsp; const sum => (a:number, b:number) => {
        return a + b;
    }<br/>
    `</pre>`<br/>
    `</code>`

<pre>
<code>
const sum => (a:number, b:number) => {
    return a + b;
}
</pre>
</code>
    
<br>

-  <br/>` ``` ` <br/>
    &nbsp; &nbsp;  const minus => (a:number, b:number) => {
        return a - b;
    } <br/>
  ` ``` `

```
    const minus => (a:number, b:number) => {
        return a - b;
    }
```

<br>
<br>


# #  `수평선 (ㅡ)`

    <hr/>
    * * *
    ****
    - - -
    ------

<hr/>

* * *
****
- - -
------    

    
<br>
<br>



# #  `링크 ([])`

    [name][val]
    [val]: url "tooltip" 

    Go Page: [Naver][link]

    [link]: https://naver.com "Go Naver" 

* Go Page: [Naver][link]

[link]: https://naver.com "Go naver" 

    일반적인 URL 혹은 이메일주소 링크를 형성

* url: <http://example.com/>
* 이메일: <email@example.com>

  
<br>
<br>



# #  `Hylight (**)`

    *First Contents*
    _Second Contents_
    **Third Contents**
    __Fourth Contents__
    ~~Fifth Contents~~

*First Contents* <br/>
_Second Contents_ <br/>
**Third Contents** <br/>
__Fourth Contents__ <br/>
~~Fifth Contents~~
  
<br>
<br>



# #  `이미지 (url)`

    ![alt](Image/CG.png "options Title")
    <img src="../Image/CG.png" width="200px" height="200px" />
    

![alt](/Image/CG.png "options Title")

<img src="../Image/CG.png" width="200px" height="200px" />

<br>
<br>

* `![]()` 형식은 size 조절 불가능
* size 조절을 하고싶으면 `<img>` 를 사용


# # `색상 (style)`

    <span style="color: red">red</span>
    <span style="color: blue">blue</span>
    <span style="color: green">green</span>
    <span style="color: gray">gray</span>
    <span style="color: yellow">yellow</span>

&nbsp;&nbsp;<span style="color: red">red</span> <br/>
&nbsp;&nbsp;<span style="color: blue">blue</span>  <br/>
&nbsp;&nbsp;<span style="color: green">green</span> <br/>
&nbsp;&nbsp;<span style="color: gray">gray</span> <br/>
&nbsp;&nbsp;<span style="color: yellow">yellow</span>

<br/>
<br/>

# # `하이라이트 (style)`

    <span style="background-color: red">red</span>
    <span style="background-color: blue">blue</span>
    <span style="background-color: green">green</span>
    <span style="background-color: gray">gray</span>
    <span style="background-color: yellow">yellow</span>

&nbsp;&nbsp;<span style="background-color: red">red</span> <br/>
&nbsp;&nbsp;<span style="background-color: blue">blue</span> <br/>
&nbsp;&nbsp;<span style="background-color: green">green</span> <br/>
&nbsp;&nbsp;<span style="background-color: gray">gray</span> <br/>
&nbsp;&nbsp;<span style="background-color: yellow">yellow</span>