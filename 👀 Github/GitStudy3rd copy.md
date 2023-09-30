<img src="../Image/github_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Git Study 3.0`

<br>

> ### **분산 버전 관리 시스템**

<br>
<br>

> Git Bash 는 CLI 프로그램

<br>

> 통상 원격저장소 등록 순서

- create repository GitHUb 사이트에서 생성
- git remote add origin <원격저장소 주소>
- git push -u origin master

<br>
<br>

- **`remote / push / pull 명령어`**

    - git remote
        - add <원격저장소 이름> <원격저장소 주소>
            - 원격저장소 등록
            - 여러 원격 저장소 등록 가능 (이름은 고유)
            - 통상 첫 원격저장소 origin 으로 지정
        - -v
            - 원격저장소 목록 보기

<br>


- **`clone 명령어`**

    - git clone
        - <저장소 주소> <클론 이름>
            - 원격 저장소가 아니고 로컬 저장소도 OK
            - 새로운 이름
        - -v
            - 원격저장소 목록 보기


<br>

> Q. 클론을 사용하는 이유 ?

```
A.  1) 코드를 로컬 환경에서 작업하기 위해
         ㄴ> 코드를 자유롭게 수정, 테스트, 개발
             로컬에서 작업하면 개발 속도가 향상 
             인터넷 연결이 끊겨도 작업을 계속 가능

    2) 프로젝트에 기여하기 위해
         ㄴ> 로컬에서 변경 사항을 만든 후, 
             이를 원격 저장소에 푸시하여 Pull Request를 생성

    3) 백업 목적으로
    4) 다른 브랜치나 태그 탐색하기 위해
    
    요약 )
    개발자가 원격 저장소의 코드를 로컬 환경에서 안전하게 작업하거나 
    탐색할 수 있게 해주며, 오픈 소스 프로젝트에 기여하거나, 
    코드를 학습, 분석하기에도 유용
```