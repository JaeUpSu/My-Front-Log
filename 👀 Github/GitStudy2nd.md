<img src="../Image/github_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Git Study 2.0`

<br>

> ### **분산 버전 관리 시스템**

<br>

> Git Bash 는 CLI 프로그램

<br>

- **`Linux 명령어`**

    - pwd
        - 현재 폴더 위치 확인
    - ls  
        - 현재 폴더의 파일 목록을 확인
    - cd /
        - 홈 폴더로 이동
    - cd 폴더 이름  
        - 특정 폴더로 이동
    - cd .. 
        - 상위 폴더로 이동
    - mkdir 새 폴더 이름
        - 새 폴더 만들기
    - echo "Hello"
        - 화면에 Hello 출력 


<br>

- **`기본 명령어`**

    - git status
        - GIt 의 워킹트리의 상태를 보는 명령
    - git status -s
        - GIt 의 워킹트리의 상태를 짧게 요약해서 보는 명령
    - git init
        - GIt 저장소 생성
            - 숨김폴더로 .git 폴더 생성
    
    <br>

    - git config &nbsp; ( 우선순위 : 지역 > 전역 > 시스템 )
        - --global 
            - <옵션명>
                - 지정 전역 옵션 내용 보기
            - <옵션명> <새로운 값>
                - 지정 전역 옵션 내용 새로운 값으로 설정
            - --unset <옵션명>
                - 지정 전역 옵션 내용 삭제
        - --local
            - <옵션명>
                - 지정 지역 옵션 내용 보기
            - <옵션명> <새로운 값>
                - 지정 지역 옵션 내용 새로운 값으로 설정
            - --unset <옵션명>
                - 지정 지역 옵션 내용 삭제
        - --system
            - <옵션명>
                - 지정 시스템 옵션 내용 보기
            - <옵션명> <새로운 값>
                - 지정 시스템 옵션 내용 새로운 값으로 설정
            - --unset <옵션명>
                - 지정 시스템 옵션 내용 삭제
        - --list
            - 현재 프로젝트의 모든 옵션 보기
    
    <br>

    - git add 파일1 파일2 &nbsp; ( 파일명이 아닌 마침표로 하면 모든 파일 )
        - 스테이지에 파일들을 추가 

    - git commit
        - 스테이지에 있는 파일들을 커밋
    - git commit -a
        - add 명려을 생략하고 바로 커밋하고 싶을 때     
    - git push -u [원격 저장소 명] [브랜치 이름]
        - 현 브랜치에서 새로 생성한 커밋들을 원격 저장소에 업로드
        - -u 옵션으로 브랜치의 업스트림을 등록 가능
        - 한 번 등록 후 git push 만 입력해도 됨
    - git pull
        - 원격 저장소의 변경 사항을 워킹 트리에 반영
        - git fetch + git merge 명령
    - git fetch [원격 저장소 별명] [브랜치 이름]
        - 원격 저장소의 브랜치와 커밋들을 로컬저장소와 동기화
        - 옵션 생략시 모든 브랜치를 가져옴
    - git merge 브랜치 이름
        - 지정 브랜치의 커밋들을 현재 브랜치 및 워킹트리에 반영
    - git reset [파일명]
        - 스테이지 영역에 있는 파일을 언스테이징
        - 워킹트리 내용 변경 x
        - 옵션 생력시 전부 내림
    - git log
        - HEAD 와 관련된 커밋들이 자세히 나옴
    - git log --oneline
        - 간단한 커밋 해시와 제목만 보고 싶을 때
    - git log --oneline -n5
        - 내 브랜치 최신 커밋 5개만 보고 싶을 때

<br>

> Q. 좋은 커밋 메시지의 7가지 규칙은 ?

```
A.  1) 제목과 본문을 빈 줄로 분리
    2) 제목은 50자 이상
    3) 제목을 영어로 쓸 경우 첫글자 대문자
    4) 제목에는 마침표 X
    5) 제목을 영어로 쓰는 경우 동사원형 시작
    6) 본문을 72자 단위로 줄 바꿈
    7) 어떻게 보다 무엇을 왜로 설명
```