# TIP 
```
프레임워크는 언제든지 바뀔 수 있다.

Fundamental 한 개념을 학습하자.

내가 참여한 프로젝트라면 
직접 구현한 기능이 아니더라도 
전반적인 Flow 를 설명할 수 있어야한다.
```

<BR>

## Q. HTTP 와 HTTPS 의 차이가 무엇인가요?
<BR>

### &nbsp;&nbsp; `A. 데이터 전송 보안이 가장 핵심 차이`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `HTTPS 는 전송 중 데이터를 암호화`

<BR>

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `+ 포트번호, URL, 인증서 유무의 차이`
<BR>

```
 <🎙️ Answer >

 둘다 WWW 를 통해 클라이언트와 서버간에
 하이퍼텍스트 요청을 전송하는데 사용되는 프로토콜

 (웹 서비스와 웹 페이지의 탐색 및 
   소비 사용가능한 방식으로 데이터 제공)

 
 HTTPS 는 HTTP 의 보안버전
 
 "보안 조치를 중심으로 몇 가지 중요한 차이 존재"
 
 HTTPS 는 SSL/TLS 를 사용하여 
 HTTP 요청 및 응답을 암호화
 데이터의 보안 유지, 무결성 유지
 

 1 ) 데이터 전송 보안
        - HTTP 는 보안 암호화 없이 작동하므로 
          데이터 가로채기와 변경에 취약

        - HTTPS 는 전송 중 데이터를 암호화
          중요한 정보를 전송하기 위한 보안 채널 제공
        
 2 ) 포트
        - HTTP 는 80 포트 사용
        
        - HTTPS 는 443 포트 사용

 3 ) URL 구성표
        - HTTP 는 http://

        - HTTPS 는 https://

 4 ) 인증서
        - HTTP 는 CA 로부터 인증서 X
        
        - HTTPS 는 CA 로부터 인증서 O

 5 ) 속도
        - HTTPS 가 데이터의 암호화 및 
          암호 해독이 필요하므로 더 느릴 수 있으나
          최신 서버의 네트워크에서는 이 차이가 최소화


 ! 특히 HTTPS 가 필요한 상황

    로그인 자격증명, 개인 사용자 세부 정보, 
    결제 정보 등과 같은 민감한 데이터 처리를 할 때 
    HTTPS 를 사용하는 것이 좋음


 ! 탈취했을 때 차이

    HTTP 데이터는 일반 텍스트로 전송되기 때문에
    공격자가 전송중인 데이터를 읽고 잠재적으로
    변경가능

    HTTPS 는 전송중인 데이터를 암호화하여
    공격자가 통신을 가로챌 수 있더라도
    데이터를 읽거나 변경할 수 없도록 하여 보호, 
    신뢰성 제공
```
<br>

## Q. HTTPS 를 호스팅 했을 때 어떻게 하나요?
<BR>

### &nbsp;&nbsp; `A. CA 기관에 SSL/TLS 인증서를 받아`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `서버에 파일 추가 및 구성`
<BR>

```
 <🎙️ Answer >
 
 1. SSL/TLS 인증서 받기
        CA 기관으로 부터 발급받기

 2. SSL/TLS 인증서 설치
        서버에 인증서 파일 추가

 3. 서버 구성 업데이트
        포트 80 대신 포트 443에 수신하도록 
        서버 구성 파일 업데이트

 4. 웹 사이트 코드 업데이트
        모든 리소스가 HTTPS 를 통해 
        올바르게 작동하도록 웹 사이트 코드 업데이트

 5. 설정 테스트
        사이트를 철저히 테스트하여 
        HTTPS 올바르게 작동되는지 확인

```
<br>

## Q. Virtual Dom 을 설명해주세요
<BR>

### &nbsp;&nbsp; `A. 실제 DOM의 직접 조작을 최소화하기 위해`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Virtual DOM 을 통한 상태 변화 유무로`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `실제 DOM 을 업데이트하는 방식`
<BR>

```
 <🎙️ Answer >
 
 UI 의 이상적인 또는 가상표현이 메모리에 유지되고
 React.js 와 같은 라이브러리에 실제 DOM 과 
 동기화되는 프로그래밍 개념 => 화해

 주요 이점은 최적화와 성능
 
 JavaScript 의 많은 app 에서 DOM 을 
 직접 조작하는 것은 느린 경향

 실제 DOM 에 직접 쓰는 대신 React 구성 요소는
 Virtual DOM 에 렌더링

 실제 DOM의 직접 조작을 최소화하여 더 나은 성능과
 더 간단한 프로그래밍 모델 가능

 
 
 1 ) 
 컴포넌트의 상태가 변경이 되면 해당 컴포넌트의 
 가상 DOM 이 업데이트 되어 새 UI 를 반영 (JSX)

 2 )
 Diffing 알고리즘을 실행하여 Virtual DOM 에 
 변경 사항 식별
 (새 Virtual DOM 과 이전 Virtual DOM 의 스냅샷 비교)

 3 )
 React 는 가장 효율적인 방법으로 Virtual DOM 과 
 일치하도록 실제 DOM 을 업데이트 
 (최소 변경 집합 계산, 조정)

 4 )
 변경이 필요한 부분만 실제 DOM 에 업데이트
 실제 DOM 의 직접 조작 최소화, 성능 UP

 5 )
 UI 동기화
```
<br>

## Q. Virtual Dom 과 연관지어 React 의 상태관리는 불변성이라는데 연관지어서 로직과 이유를 말해주세요.
<BR>

### &nbsp;&nbsp; `A. 실제 DOM 을 직접 조작하는 것이 아닌`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `가상 DOM 으로 변화감지 용이, 최적화된 `
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `렌더링, 시간여행 디버깅 및 롤백 용이`
<BR>

```
 <🎙️ Answer >

 React에서 상태는 종종 "불변"으로 설명
 이는 직접 변경할 수 없음을 의미
 
 현재 상태를 직접 수정하는 대신 새 상태를 생성 
 이 원칙은 React 프로그래밍 모델의 중요한 부분이며 
 React가 Virtual DOM과 상호 작용하는 방식에도 매우 중요

 단순성, 성능, 디버깅 관점에서 이점

 ---

 1. 변화 감지 용이
    
    상태가 가변적이면 깊은 비교를 해야하지만
    상태가 불변성이라면 상태 객체의 참조가
    바뀌었는지만 확인하면 됨

 2. 최적화된 렌더링

    어떤 컴포넌트를 다시 렌더링해야 할지를
    효과적으로 판단하는데 도움을 줌

 3. time travel 디버깅과 롤백 용이

    불변성을 지키면서 상태를 관리하면
    이전 상태를 쉽게 복원 가능

    사용자의 액션을 취소하거나 재생하는 
    기능을 구현하기 용이


 [결론]
 변화 감지 용이 / 최적화된 렌더링
 time travel 디버깅과 롤백 용이
```
<br>

## Q. API 설명해주세요.
<BR>

### &nbsp;&nbsp; `A. 한 프로그램에서 다른 프로그램으로 데이터를 주고 받기`

<br>

```
 <🎙️ Answer >

 Application Programming Interface

 한 프로그램에서 다른 프로그램으로 데이터를
 주고 받기 위한 방법

 프로그램 -(요청)->     API   -(요청)->  프로그램
        <-(데이터)-         <-(데이터)-
```
<br>

## Q. REST ful 이 어떤 정의와 논리를 가지는지 설명해주세요.
<BR>

### &nbsp;&nbsp; `A. 표현된 상태로 전송`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `HTTP URL 를 통한 자원(리소스) 명시`

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `HTTP Method (GET/POST/PUT/DELETE)로`

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `해당 자원에 대한 CRUD Operation 을 적용`

<br>

```
 <🎙️ Answer >
 
 표현된 상태로 전송
 
 두 컴퓨터 시스템이 인터넷을 통해 
 정보를 안전하게 교환하기 위해 
 사용하는 인터페이스

 다음과 같은 구성요소와 원칙을 가짐


 A. 자원과 URI
    웹에 존재하는 모든 자원을 각각 고유 URI
    를 부여하여 표현

 B. 표현
    클라이언트와 서버가 데이터를 주고받는
    형태를 의미 (JSON / XML)

 C. *상태 전이
    REST 는 상태를 가지지 않음
    각 요청은 다른 요청에 대한 정보 X
    확장성 높이며 간단하게 유지 가능

 D. 메시지는 자기 설명적
    각 메시지는 해당 메시지를
    어떻게 처리해야 하는지
    충분한 정보를 포함

 E. *클라이언트 서버 구조
    클라이언트와 서버는 독립적으로 행동

    REST 서버는 API 를 제공,
    클라이언트는 사용자 인터페이스와 
    책임을 가짐
    
 F. *캐시 가능
    HTTP 에서와 같이 클라이언트는 응답을
    캐싱하고 재사용 가능
    
 G. *계층형 구조
    어플리케이션은 클라이언트와 
    서버 사이 중개자에 관계없이 동일하게 작동
    
    클라이언트는 대상서버만 알면 됨,
    그앞에 어떤 서버들이 또는 프록시가
    있더라도 알필요 X
    
 H. *Uniform Interface
    클라이언트와 서버는 서로 보편적이고 
    예측가능하게 상호작용
    
    URI 로 지정한 리소스에 대한 조직 통일
    한정적인 인터페이스로 수행
    
    HTTP 표준에 따라 
    GET/POST/PUT/DELETE 등 메소드 이용

 ---


 1. URI 를 통해 자원을 식별
    Client =  (URI/user/1)    => Server
    Client <= (user table 정보) = Server

 2. GET/POST/PUT/DELETE 등을 통한 
    메소드 행위 지정
        (GET/user/1)

 3. Client 요청에 대한 적절한 응답
    여러 형태의 표현으로 나타내어 보냄
        (HTTP 1.1 200 OK)
        (Content Type:applicaion/json)
        ({"name":"me"})


 -> HTTP URL 를 통한 자원(리소스) 명시
 -> HTTP Method (GET/POST/PUT/DELETE)로
 -> 해당 자원에 대한 CRUD Operation 을 적용

 URI 는 동사보다는 명사 명시
 URI 에 버전 정보 포함
 행위는 HTTP 메소드를 통해 명시

 # REST API
    - 기술이 아닌 REST 아키텍처 스타일에 
      부합한 API

    - REST 아키텍쳐 스타일을 잘 따른 API

! 오늘날의 대부분 REST 를 잘 따르지 못함
 - 제약조건 중 Self0descriptive 와 HATEOAS 
   만족 X
 - 무조건적으로 REST API 가 최적은 아님
 - 다른 API 표준을 선택하기도 함 (GraphQL)
```
<br>

## Q. REST ful 과 CRUD 를 맵핑해서 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. Create <=> POST/PUT`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Read <=> GET`

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Update <=> PUT/POST/PATCH`

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Delete <=> DELETE`

<br>

## Q. REST ful 이 어떤 이점이 있는지 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. 확장성과 유연성`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `독립성`

<br>

```
 <🎙️ Answer >
 
 언어와 플랫폼 독립적
    REST는 HTTP를 통해 데이터를 전송, 
    어떤 언어나 플랫폼에서도 사용
 
 확장성과 유연성
    REST는 상태를 저장하지 않는다는 특징 
    덕분에 서버 측의 확장성이 향상
    
    또한, 데이터 형식(JSON, XML 등)이나 
    통신 방식(GET, POST, PUT 등) 유연

 독립성
    서버와 클라이언트의 분리
    각각을 독립적으로 개발하고 업데이트 가능
    이는 유지보수를 쉽고 개발 효율성을 높임

 캐싱 가능
    HTTP 프로토콜을 그대로 사용
    HTTP의 캐싱 기능을 그대로 활용
    이는 클라이언트의 응답 속도를 향상, 
    서버의 부하를 줄일 수 있음

 직관적인 인터페이스
    RESTful API는 일관된 인터페이스를 
    가지고 있어 사용하기 쉽고 이해하기 쉬움 
    
    예를 들어, 
    GET /users는 사용자 목록을 가져오고, 
    POST /users는 새 사용자를 생성하는 등, 
    
    URI와 HTTP 메소드만 봐도 
    해당 API가 어떤 작업을 하는지 알 수 있음

 디버깅 및 테스팅 용이
    HTTP 프로토콜 위에서 작동
    표준 HTTP 디버깅 도구를 사용하여 
    API를 쉽게 테스트하고 디버그 가능

---

모든 상황에 RESTful이 최선의 선택 X 
상황에 따라서는 SOAP, GraphQL 등의 
다른 API 스타일이 더 적합
```
<br>

## Q. PUT 과 PATCH 가 어떻게 다른지 말해주세요.

<BR>

### &nbsp;&nbsp; `A. PATCH 는 리소스 일부`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `PUT 은 전체 리소스를 교체 업데이트`

<br>

```
 <🎙️ Answer >
 
 PATCH
  리소스의 일부를 업데이트 하는 데 사용
 
 반면 
 
 PUT
  전체 리소스를 교체 업데이트 하는 데만 사용
```
<br>

## Q. Local Storage 와 Session Storage 그리고 Cookie 에 대해 차이를 말해주세요.

<BR>

### &nbsp;&nbsp; `A. 데이터의 유지 기간과 용량`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `각기 다른 보안`

<br>

```
 <🎙️ Answer >
 데이터의 유지 기간과 용량, 
 그리고 데이터가 서버와 클라이언트 사이에서 
 어떻게 교환되는지에 따라 
 각각 적합한 사용 사례가 다름


* Local Storage
    Web Storage API의 일부
    브라우저에서 키-값 쌍을 저장하는 데 사용
    
    이 데이터는 사용자가 브라우저를 닫거나 
    컴퓨터를 재부팅해도 유지
    
    하지만 사용자가 브라우저의 데이터를 
    명시적으로 지우지 않는 한 
    
    "영구적"
    
    이로 인해 Local Storage는 
    사용자가 사이트에서 설정한 
    환경 설정 같은 영구적인 
    데이터를 저장하는 데 유용
    
    각 도메인마다 
    보통 5MB 정도의 데이터를 저장

* Session Storage
    Session Storage 역시 
    Web Storage API의 일부
    
    이는 Local Storage와 유사하게 작동
    
    "브라우저를 닫거나 탭을 닫을 때" 
    
    저장된 데이터가 사라짐 
    
    이로 인해 Session Storage는 
    웹사이트의 단일 세션(방문) 동안 
    유지해야 하는 데이터를 저장하는 데 유용
    예를 들면 장바구니 같은 것이 이에 해당

* Cookies
    Cookies는 웹 사이트가 
    사용자의 브라우저에 저장하는 
    작은 텍스트 파일
    
    이는 주로 사용자가 
    사이트를 방문할 때마다 
    그들을 식별하는 데 사용
    
    Cookies는 HTTP 요청과 
    응답 헤더에 자동적으로 포함
    서버 측에서 클라이언트의 
    상태 정보를 유지하거나 추적하는데 사용
    
    쿠키는 만료 날짜가 있어서 
    그 날짜가 지나면 자동으로 삭제
    쿠키의 크기는 보통 4KB로 제한
```
<br>

## Q. Local Storage 와 Session Storage 그리고 Cookie 에 대해 보안의 차이에 대해서 구체적으로 말해주세요.

<BR>

### &nbsp;&nbsp; `A. storage 는 js 접근 가능`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `XSS 공격에 취약`

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Cookie 는 중간자 공격 취약`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `이를 방지하기 위해 HTTPS 연결`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `XSS 공격은 HTTP Only 로 방지`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `CSRF 공격에 취약`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `samsite 속성으로 방지 가능`

<br>

```
 <🎙️ Answer >
 
 Local Storage와 Session Storage
    Local Storage와 Session Storage는 
    클라이언트 측에서만 접근이 가능, 
    HTTP를 통해 전송되지 않음 
    
    이는 사용자의 브라우저에서 
    데이터가 노출되는 것을 일정 부분 방지
    
    하지만 이 데이터는 
    JavaScript를 통해 접근 가능
    
    Cross-Site Scripting(XSS) 공격에 취약
    XSS 공격자가 악성 스크립트를 성공적으로 
    실행시키면 사용자의 Local Storage와 
    Session Storage 데이터에 접근 가능


 Cookies
    Cookies는 각 HTTP 요청과 함께 
    서버로 전송
    
    중간자 공격(MitM)에 취약할 수 있음 
    이러한 공격자는 사용자와 서버 사이에 
    끼어들어 통신 내용을 엿보거나 변조 가능 
    
    이를 방지하기 위해 Secure Flag가 설정된 
    쿠키는 HTTPS 연결을 통해서만 전송
    
    또한, HttpOnly Flag가 설정된 쿠키는 
    JavaScript를 통해 접근 불가능 
    XSS 공격을 방지
    
    하지만 CSRF 공격에 취약
    CSRF 공격은 공격자가 
    사용자의 신원을 도용하여 
    악의적인 요청을 보내는 방식
    
    이를 방지하기 위해 SameSite 속성을 
    이용한 쿠키 설정을 사용하거나 
    CSRF 토큰을 사용할 수 있음


따라서, 이러한 스토리지 방식을 사용할 때는 
각각의 보안 측면을 반드시 고려

특히 민감한 정보를 저장하는 경우에는 
추가적인 보안 조치가 필요하며, 
가능한한 서버 측에 저장하는 것이 보안에 더 효과적
```
<br>

## Q. Local Storage 와 Session Storage 그리고 Cookie 에 대해 휘발성의 차이에 대해서 구체적으로 말해주세요.

<BR>

### &nbsp;&nbsp; `A. Local => 영구적, 직접 삭제`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Session => 브라우저 또는 탭을 닫을 때 삭제`

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Cookie => 만료날짜가 지나면 삭제`

<br>

## Q. HTTP Only 에 대해서 어떤 논리와 어떻게 사용되는지 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. XSS 공격을 방지`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `클라이언트 측 스크립트(JavaScript )를`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ` 통해 접근 불가능`

<br>

```
 <🎙️ Answer >
 
  웹 브라우저가 쿠키에 대한 
  접근을 제한하는 데 사용되는 속성

  쿠키는 HTTP 및 HTTPS 요청과 
  함께만 서버로 전송
  
  즉, JavaScript의 document.cookie와 같은 
  클라이언트 측 스크립트를 통해 접근 불가능

  XSS 공격을 방지하는데 중요한 역할
   ㄴ> 악성 스크립트를 삽입하여 
       사용자의 정보를 탈취하는 보안 위협

  JavaScript를 통해 읽을 수 없음

  HttpOnly 쿠키는 서버에서 
  쿠키를 설정할 때 사용

  axios로 서버에 요청을 보낼 때 
  웹 브라우저의 쿠키를 자동으로 포함 가능
  
  axios의 withCredentials 옵션을 true 설정
  axios.get('http://example.com', { 
    withCredentials: true 
  });

```
<br>

## Q. 인증과 인가에 대한 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. 인증은 사실 유무 확인`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `인가는 권한 유무 확인`

<br>

```
 <🎙️ Answer >
 
 인증 : 어떤 사실을 진짜인지 증명하는 과정
        사용자의 신원 확인

 인가 : 접근 권한을 부여하는 과정 
        어떤 개체가 어떤 리소스에 
        접근 가능한지
        혹은 어떤 동작이 수행 가능한지

 -> 무단 접근 및 악용 방지

 * 인증 후 인가가 이루어짐

 [세션 기반 인증]
  클라이언트와 서버 간 상태 유지
  1. 사용자 로그인 요청
  2. 인증 및 세션 생성
  3. 세션 ID 전달
  4. 서버에 요청을 보낼 때마다 
     세션 ID 를 함께 전달

  Server - 웹사이트 제공 -> Client
  Server <- 로그인 요청 - Client
  Server - 세션 생성 및 유지, 응답 -> Client
  Server <- 요청 - Client
  Server - 세션읽고, 응답 -> Client

  장점 ) 상태 유지, 간단한 구현
  단점 ) 서버부하, 확장성 제한, CORS 문제

  

 [토큰 기반 인증]
  클라이언트와 서버 간 상태 유지 X
  1. 사용자 로그인 요청
  2. 인증 및 토큰 생성
  3. 토큰 전달
  4. 서버에 요청을 보낼 때마다 
     토큰을 함께 전달

  Server - 웹사이트 제공 -> Client
  Server <- 로그인 요청 - Client
  Server - 토큰 생성, 응답 -> Client (토큰 저장)
  Server <- 토큰과 함께 요청 - Client
  Server - 토큰 검증 응답 -> Client

  장점 ) 상태 유지 X, 다양한 클라이언트 호환
         CORS 문제 해결
  단점 ) 사용자 인증 상태 실시간 추적 불가능
         보안 및 만료 기간 주의
         검증을 위한 DB에서 사용자 정보 조회
         (성능 저하 유발)
```
<br>

## Q. JWT 의 Flow 는 어떻게 되나요?

<BR>

### &nbsp;&nbsp; `A. 로그인 요청 -> 인증(DB 정보)`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ` -> jwt생성-> 발행 -> 저장`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ` -> 인증요청 -> jwt 검증`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ` -> 인증된 요청 처리`

<br>

```
 <🎙️ Answer >

 Json Web Token
 
 정의 - 인증에 필요한 정보들을
        암호화 시킨 Json 토큰 

 구조 - Header.Payload.Siganture
        (헤더.내용.서명)
        (.을 구분자로 세가지 문자열 조합)
        (하나의 문자열로 저장)

 헤더 (토큰의 유형, 사용 서명 알고리즘)
 내용 (Claim, 사용자 권한 정보와 데이터)
 서명 (인코딩한 문자열, 비밀키)

 * secrete key 를 통해 발급하고 인증


1. 로그인 요청
    사용자는 아이디와 비밀번호를 입력
    클라이언트에게 로그인 요청
    이 정보는 서버로 전송

2. 인증 및 토큰 생성
    서버는 받은 아이디와 비밀번호를 확인
    사용자를 인증
    
    사용자가 올바르게 인증되면, 
    서버는 Token (access/refresh)을 생성

3. 토큰 발행
    서버는 생성된 access 토큰과 
    리프레시 토큰을 클라이언트에게 반환
    
4. 토큰 저장
    클라이언트는 받은 토큰들을 저장
    웹에서는 보통 쿠키나 웹 스토리지에 토큰을 저장
    
5. 인증 요청
    클라이언트가 서버에 요청을 보낼 때마다 
    access 토큰을 요청 헤더에 포함하여 전달

6. 토큰 만료 확인
    서버는 받은 access 토큰이 만료되었는지 확인 
    만료되었다면 클라이언트에게 
    액세스 토큰이 만료되었다는 응답을 전달
    401 Error (Unauthorized) 반환

7. 액세스 토큰 재발급 요청
    클라이언트는 만료 응답을 받으면 
    저장해둔 리프레시 토큰을 이용해 
    새로운 액세스 토큰을 요청

8. 리프레시 토큰 확인 및 액세스 토큰 재발급(계속)
    리프레쉬 토큰이 유효성 검사를 통과한
    토큰이라면 새로운 액세스 토큰을 생성
    클라이언트에게 반환
    
    이렇게 재발급 받은 액세스 토큰은 
    다시 요청 헤더에 포함되어 전달 가능

예외 ) 만료된 리프레시 토큰이라면 
       사용자가 다시 로그인 요청

```
<br>


## Q. JWT 에서 Refresh Token 과 Access Token 이 어떻게 활용되는지 설명해주세요.

```
@ access
일반적으로 짧은 유효 기간
사용자가 리소스에 접근할 권한을 부여하는 역할
보통 헤더에 직접적으로 포함

@ refresh
긴 유효 기간
액세스 토큰이 만료됐을 때 
새로운 액세스 토큰을 발급받는데 사용

보통 서버에 저장
가끔 헤더에 같이 저장되기도 하지만 보안 위험
```

```
 <🎙️ Answer >
 
* Access Token
 사용자의 인증 상태를 나타냄 
 사용자가 특정 리소스에 
 액세스 할 수 있는 권한을 부여하는데 사용
 
 짧은 수명을 가지고 있고, 
 일반적으로 몇 분에서 몇 시간 사이로 설정

 탈취당하더라도, 
 공격자가 제한된 시간 동안만 
 해당 토큰을 이용할 수 있도록 하기 위한 것

 사용자가 다시 로그인하지 않고 
 자동으로 새 Access Token을 얻기 위해 
 Refresh Token이 사용

* Refresh Token
 더 긴 수명
 Access Token이 만료된 후에 
 새로운 Access Token을 발급받는데 사용

 이 토큰을 사용하면, 
 사용자는 매번 자신의 아이디와 
 비밀번호를 입력하여 
 로그인 할 필요 없이 
 새 Access Token을 얻을 수 있음

 보통 서버에 저장되어 관리
 만약 유효하지 않은 Refresh Token이 
 새 Access Token을 요청하면 
 서버에서 이를 거부
 
 만약 Refresh Token이 탈취당하거나 
 잘못 사용된 것으로 의심되는 경우, 
 해당 토큰을 무효화하고 
 사용자에게 새로운 Refresh Token을 발급

 가장 안전한 방법은 
 Refresh Token을 클라이언트 측에서 
 직접 액세스하지 못하게 하는 것

---

 HttpOnly 쿠키를 사용하여 
 Refresh Token을 보내고, 
 이 토큰은 서버 측에서만 읽을 수 있음

 일부 애플리케이션에서는 
 Refresh Token을 클라이언트에 전송
 클라이언트에서 이를 저장
 
 이 경우 클라이언트는 
 Refresh Token을 보관하고 
 필요할 때마다 사용 가능 
 
 이 방식은 애플리케이션 개발에 
 더 많은 유연성을 제공하지만, 
 보안 위험을 증가시킬 수 있으므로 주의가 필요
```
<br>

## Q. JWT Token 이 어떻게 만료를 확인하는지 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. JWT의 페이로드 부분에`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `저장된 exp 클레임을 검사`

<br>

```
 <🎙️ Answer >

 JWT는 만료 시간을 포함하는 
 exp라는 클레임을 가질 수 있음 
 
 exp 클레임은 토큰이 만료되는 
 UTC 시간을 나타냄 
 
 JWT를 검증할 때, 
 서버는 이 exp 클레임을 확인하여 
 토큰이 만료되었는지 판단 
```
<br>

## Q. JWT 에서 Refresh Token 과 Access Token 중에 어떤 것이 탈취당하는게 더 위험한지 설명하시오.


<BR>

### &nbsp;&nbsp; `A. refresh 토큰`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `상대적으로 긴 유효 시간을 가져서`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `계속 access 토큰을 생성 가능`

<br>

```
 <🎙️ Answer >

 일반적으로 Refresh Token이 
 탈취당하면 더 위험

 Access Token은 
 짧은 유효 시간을 가질 수 있음
 만료 시간이 지나면 더 이상 유효하지 않음

 반면에 Refresh Token은 
 긴 유효 시간을 가질 수 있음 
 이 토큰을 사용하여 
 새로운 Access Token을 생성 가능 
 
 ----

 따라서, Refresh Token이 탈취당하면 
 공격자는 새로운 Access Token을 
 계속 생성할 수 있으므로 위험도가 높음
```
<br>

## Q. JWT 에서 토큰의 탈취를 어떤식으로 할 수 있는지 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. 중간자 공격 / XSS 공격`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Phishing`

<br>

```
 <🎙️ Answer >
 
 * 중간자 공격 (MitM) 
  공격자가 사용자와 서버 사이에 위치하여
  통신을 가로채는 공격

 * XSS 공격
  악의적인 스크립트가 웹 사이트에 삽입되어
  사용자의 정보가 공격자에게 전달되는 것
  (토큰이 javascript 를 통해 접근 가능할 때)

 * Phishing
   사용자를 속여 공격자가 제어하는 
   사이트로 유도 (자격증명과 토큰 훔침)
```
<br>

## Q. JWT 에서 토큰의 탈취를 어떤식으로 보안할 수 있는지 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. HTTPS / HTTPOnly`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `교육`

<br>

```
 <🎙️ Answer >
 
 @ 방지

 - HTTPS 사용하여 모든 통신 암호화
   중간자 공격 방지 가능

 - 토큰을 HttpOnly 쿠키에 저장
   JavaScript 를 통한 접근 불가능
   XSS 공격 방지 가능

 - 사용자에게 안전한 브라우징 습관 교육
   이메일이나 웹사이트의 URL 을 
   항상 확인 강조
   피싱 공격 방지 가능
```
<br>

## Q. CRA 와 Next.js 가 어떻게 사용되는지 알려주세요.

<BR>

### &nbsp;&nbsp; `A. CRA 는 SPA 개발에 적합`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `NEXT.js 는 SSR 과 SSG 개발에 적합`

<br>

```
 <🎙️ Answer >
 
 CRA를 사용하면 
 
 Single Page Applications (SPA) 개발에 적합

 Babel, Webpack 등의 복잡한 설정 없이 
 React 애플리케이션을 빌드하고, 
 테스트하고, 배포 가능 
 
 또한, React 개발을 위한 
 최적화된 설정을 제공
 개발자는 애플리케이션 로직에 집중

 ---

 서버사이드 렌더링(SSR), 
 정적 사이트 생성(SSG), 
 Incremental Static Regeneration(ISR), 
 API 라우트 등 다양한 기능을 제공

 이런 기능들은 SEO 최적화, 성능 개선, 
 개발 생산성 향상 등에 유리
 초기페이지 로딩성능 개선
 
 Next.js는 프로젝트 생성부터 
 프로덕션 배포까지의 
 전체 웹 개발 생명주기를 지원하며, 
 TypeScript, ESLint, PostCSS 등의 
 최신 웹 기술을 쉽게 적용

 ---

 간단한 SPA를 개발할 때는 CRA가 적합

 SSR이나 SSG 기능이 
 필요한 복잡한 웹 애플리케이션을 
 개발할 때는 Next.js가 적합
```
<br>

## Q. Git 에서 PR 을 할 때 rebase 와 merge 의 차이를 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. merge : 각 브랜치의 끝 부분을 병합`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `rebase : 한 브랜치의 변경사항을 다른 브랜치에 적용`

<br>

```
 <🎙️ Answer >
 
 [merge]

 * 두 브랜치를 합치는 동작

 두 브랜치를 합칠 때 
 각 브랜치의 끝 부분을 병합하는 방법
 
 merge 명령을 실행하면, 
 두 브랜치의 변경사항을 
 모두 포함하는 새로운 커밋이 생성
 
 이 방식은 병합 과정에서 
 양쪽 브랜치의 변경 이력을 
 모두 유지하지만, 
 이 결과 복잡한 커밋 트리를 만들 수 있음

 ---

 [rebase]

 * 한 브랜치의 커밋들을 다른 브랜치 위로 옮김

 한 브랜치의 변경사항을 
 다른 브랜치에 적용하는 방법
 
 rebase는 "재배치"라는 뜻
 
 한 브랜치의 커밋을 
 '다른 브랜치 위로' 재배치
 
 이 방식은 브랜치의 
 커밋 트리를 선형적으로 생성, 
 브랜치의 변경 이력을 깔끔하게 유지 가능 
 
 하지만, rebase는 과정 중에 
 충돌이 발생하면 해결이 복잡할 수 있음 

 기존 커밋의 순서를 바꾸므로 
 히스토리를 조작하는 것과 같은 효과가 있음

 ---

 merge를 사용
 PR은 일반적으로 브랜치 간의 
 변경 사항을 병합하는 방법
 
 merge 명령을 사용하여 
 소스 브랜치의 변경 사항을 
 대상 브랜치에 적용
 
 ---

 반면에 rebase는 
 PR 전에 작업 브랜치에서 
 주로 사용
 
 rebase를 사용하면 
 작업 브랜치를 최신 상태로 유지
 변경 사항을 적용 가능 
 
 rebase 후에는 PR을 생성하여 
 merge할 수 있음
```
<br>

## Q. Promises 를 설명해주세요.

<BR>

### &nbsp;&nbsp; `A. 비동기 작업의 최종 완료`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `또는 실패를 나타내는 객체`

<BR>

```
 <🎙️ Answer >
 
  비동기 작업의 최종 완료 또는 실패를 나타내는 객체

  간단히 말하면, 
    Promise는 어떤 일이 끝날 때까지 기다렸다가, 
    그 일이 성공적으로 끝나면 그 결과를, 
    실패하면 그 원인(에러)를 반환


- Promise는 다음 중 하나의 상태를 가짐
  
  Pending(대기중)
    Promise가 아직 이행되지 않거나 
    거부되지 않은 초기 상태

  Fulfilled(이행됨)
    Promise의 작업이 성공적으로 완료

  Rejected(거부됨)
    Promise의 작업이 실패

Promise는 작업이 완료되면(이행 or 거부) 
상태를 변경하고, 

그 상태는 이후에 변경되지 않음 
이를 'Promise가 settled(결정됨)되었다'고 함

[사용하는 이유] 
    콜백 함수의 '콜백 헬'을 피하기 위함
  
        콜백 헬 -> 여러 개의 비동기 작업을 
                   순서대로 처리해야 할 때, 
                   콜백 함수가 중첩되어 
                   코드가 복잡해지는 상황
    
    작업을 특정한 순서로 실행하고 
    싶을 때 사용

        같은 턴에 수행해야할 작업이 
        많다면 프로미스를 활용해 
        다음 턴으로 미룰 수 있음
```
[선언]
```javascript
let promise = new Promise(function(resolve, reject) {
  // 비동기 작업...

  if (/* 비동기 작업이 성공적으로 끝났다면 */) {
    resolve(value); // 작업의 결과 값
  } else {
    reject(error); // 작업 중 발생한 에러
  }
});
```
[사용]
```javascript
promise
  .then(value => {
    // Promise가 이행되었을 때 실행되는 함수
  })
  .catch(error => {
    // Promise가 거부되었을 때 실행되는 함수
  });
```
<br>


## Q. aync-await 를 설명해주세요.

<BR>

### &nbsp;&nbsp; `A.  비동기 처리를 동기 처리처럼`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `보이게 하는 키워드로, Promises를 `
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `더 간결하고 이해하기 쉽게 처리하는데 사용`

<BR>

```
 <🎙️ Answer >
 
 ES8 문법
 Promise를 더 간단하고 가독성 좋게 사용

 Async 
  -> 해당 함수가 항상 Promise를 반환하도록 함

  async function foo() {
    return 1;
  }

  foo().then(alert);

Await
  -> await 키워드는 Promise가 
     settle될 때까지 기다리는 역할
  -> Promise가 이행되면 그 결과를, 
     거부되면 에러를 반환

  async function foo() {
    let promise = new Promise((resolve, reject) => {
        setTimeout(() => resolve("done!"), 1000)
    });

    let result = await promise; // Promise가 이행될 때까지 기다림

    alert(result); // "done!"
  }

  foo();


! await가 Promise가 settle될 때까지 
  실행을 중지하므로, 불필요한 대기 시간이 
  발생하지 않도록 주의
```
<br>


## Q. Cookie 와 Header 를 연관지어서 설명해주세요.
<BR>

### &nbsp;&nbsp; `A. 세션 관리나 사용자 인증 등의`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `기능을 구현하는 데 있어서 중요한 역할`

<BR>

```
 <🎙️ Answer >
 
  쿠키와 헤더는 상태를 유지하지 않는 
  HTTP 프로토콜에서 세션 관리나 
  사용자 인증 등의 기능을 구현하는 데 
  있어서 중요한 역할

  웹 애플리케이션에서는 사용자를 구분
  사용자의 세션을 관리해야 하는 경우가 많음 
  이때 사용되는 것 => 쿠키

  쿠키는 클라이언트에 저장되어 이후 
  요청 때마다 자동으로 Cookie 헤더에 
  포함되어 서버에 전달
  
  쿠키는 클라이언트에 저장되어 
  이후 요청 때마다 자동으로 Cookie 헤더에 
  포함되어 서버에 전달

  => 사용자의 브라우저에 저장돼 
     탈취 가능성 존재
      => 이런 문제 해결 : HttpOnly 
          => HttpOnly쿠키는 JavaScript에서
             접근할 수 없고 HTTP/HTTPS 요청
             통해서만 전송
```
<br>


## Q. CorsHeader 에 대해 설명해주세요.
<BR>

### &nbsp;&nbsp; `A. 다른 도메인에서 리소스를`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `공유할 수 있도록 해주는 웹 표준`

<BR>

```
 <🎙️ Answer >
 
 CORS(Cross-Origin Resource Sharing)는 
 다른 도메인에서 리소스를 공유할 수 있도록 
 해주는 웹 표준

 웹 페이지는 기본적으로 동일 출처 정책
 (Same-Origin Policy)을 따르기 때문에, 
 같은 출처의 리소스만 가져올 수 있음

 => 보안상의 이유로, 스크립트가 
    악의적인 행동을 하는 것을 막기 위한 것


 => 그래서 API 등을 통해 다른 도메인에서 
    리소스를 사용하는 데 어려움 

 => 이 문제를 해결하기 위해 CORS가 등장

 => CORS는 서버에서 특정 헤더를 설정함으로써, 
    다른 도메인의 리소스를 공유하도록 허용

 => Access-Control-Allow-Origin: *
    모든 출처에서의 요청을 허용

 => Access-Control-Allow-Methods는 
    어떤 HTTP 메서드
    (GET, POST, PUT, DELETE 등)를 
    허용할지 지정

 => Access-Control-Allow-Headers
        : Content-Type
    허용되는 요청 헤더를 지정

 CORS 설정은 일반적으로 서버 측에서 구현 
 그러나 미들웨어 또는 클라우드 서비스를 
 사용해서도 구현가능
```
<br>


## Q. CorsHeader 의 에러를 어떻게 확인할 수 있는지 설명해주세요.
<BR>

### &nbsp;&nbsp; `A. 웹 브라우저 콘솔에서 확인 가능`

<BR>

```
 <🎙️ Answer >
 
 웹 애플리케이션을 개발하고 테스트할 때 
 흔하게 만나는 문제 중 하나
 
 이러한 에러는 웹 브라우저 콘솔에서 
 확인 가능
 
 [해결방안]
    서버의 CORS 설정 확인
    브라우저의 네트워크 패널 확인
    'preflight' 요청 확인
    서버와 클라이언트의 프로토콜과 포트 확인
    프록시 설정
```
<br>


## Q. Proxy 에 대해 원리와 정의를 설명해주세요.
<BR>

### &nbsp;&nbsp; `A. 네트워크에서 한 컴퓨터가`
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `다른 컴퓨터의 연결을 대신하는 것`


<BR>

```
 <🎙️ Answer >
 
 프록시는
 네트워크에서 한 컴퓨터가 
 다른 컴퓨터의 연결을 대신하는 것

 프록시 서버는 
 클라이언트와 인터넷 리소스
 (예: 웹페이지, 파일, 웹서비스 등) 
 사이에서 중개자 역할

 클라이언트가 프록시 서버에 연결
 => 프록시 서버는 클라이언트 대신 
    인터넷 리소스에 연결
 =>그 결과를 클라이언트에게 전달



! 프록시는 웹 개발 환경에서도 자주 사용
    => CORS 문제를 해결하기 위해
    => 클라이언트와 서버가 같은 도메인에서 
       실행되는 것처럼 보이게 해주어 
       클라이언트의 요청을 서버로 전달
```
<br>


## Q. 개발 환경과 프로덕트 환경의 차이를 설명해주세요.
```
 <🎙️ Answer >
 
 [개발 환경]
 개발자들이 새로운 기능을 개발하거나 
 기존의 버그를 수정하는 곳
 
 이 환경에서 개발자들은 코드를 작성
 테스트하며, 코드의 수정사항을 추적

 [프로덕션 환경]
 최종 사용자에게 제공되는, 
 실제 운영되는 애플리케이션
 
 이 환경에서의 애플리케이션은 
 안정적이어야 하며, 
 테스트를 통과한 코드만이 배포되어야 함
 또한, 보안 및 성능 최적화가 중요한 요소




---


애플리케이션을 개발하면서 개발 환경과 프로덕션 환경을 분리하는 것은 매우 중요합니다. 이렇게 환경을 분리하면 개발 프로세스가 더욱 효율적이고 안전해집니다.

환경 설정을 분리하는 가장 일반적인 방법 중 하나는 각 환경에 대한 설정을 담고 있는 별도의 설정 파일을 가지는 것입니다. 예를 들어, Node.js 어플리케이션에서는 다음과 같이 환경별로 서로 다른 설정을 적용할 수 있습니다.

.env.development 파일에는 개발 환경에서 사용될 설정을 정의합니다. 예를 들어, 로컬 데이터베이스 연결 문자열, 개발용 API 키 등을 포함시킬 수 있습니다.

.env.production 파일에는 프로덕션 환경에서 사용될 설정을 정의합니다. 예를 들어, 실제 서비스에 사용되는 데이터베이스 연결 문자열, 실제 API 키 등을 포함시킬 수 있습니다.

이러한 설정은 어플리케이션의 초기화 과정에서 불러와지고, 어플리케이션 코드 내에서 사용됩니다. 이를 통해 개발자는 코드를 변경하지 않고도 각 환경에 맞는 설정을 적용할 수 있음
```
<br>
