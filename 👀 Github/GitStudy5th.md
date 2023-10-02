<img src="../Image/github_logo.jpg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Git Study 5.0`

<br>

> ### **분산 버전 관리 시스템**

<br>
<br>

> ### **CLI 로 Checkout 하기**

<br>
<br>

- **`새로운 커밋을 생성하면`**

    - 새로 커밋 생성하면 그 커밋의 부모는 언제나 이전 HEAD 커밋
    - 커밋이 생성되면 HEAD 는 새로운 커밋으로 갱신
    - HEAD 가 가리키는 브랜치도 HEAD 와 함께 새로운 커밋


<br>



- **`브랜치 되돌리기`**

    - git reset --hard <이동할 커밋 체크섬>
    - git reset --hard HEAD~2
        - 현 브랜치를 두 단계 이전으로 되돌리기
        - master 브랜치가 옮겨짐

        

<br>

- **`rebase 명령어 맛보기`**

    - git rebase <대상 브랜치>
        - 현재 브랜치에만 있는 새로운 커밋을 대상 브랜치 위로 재배치
        - 재배치할 커밋이 없는 경우 동작 X

        

<br>

- **`tag 명령어`**

    - Git 기록의 특정 지점을 가리키는 참조
    - 태그 지정은 일반적으로 버전 릴리스와 같은 기록의 특정 지점을 캡처하는 데 사용

    - git tag -a -m "간단한 메시지" <태그이름> [브랜치 또는 체크섬]
        - -a 로 주석 있는 (annotated) 태그 생성
        - 메시지와 태그 이름은 필수
        - 브랜치 이름을 생략하면 HEAD 에 태그 생성

    - 태그 사용
        - 순서
            - git log --oneline &nbsp; &nbsp; &nbsp;# 로그확인
            - git tag -a -m "첫 번째 태그" v0.1 &nbsp; &nbsp; &nbsp;# 주석있는 태그 생성
            - git push origin v0.1  &nbsp; &nbsp; &nbsp;# 태그 푸시

    - 특징
        - `스냅샷`<br>태그는 일반적으로 릴리스에 사용되는 특정 시점의 코드 스냅샷 역할
        - `불변 참조`<br> 태그는 불변<br> 즉, 태그가 가리키는 분기가 변경되더라도 태그는 변경 X

        <br>

    - 사용되는 경우
        - 릴리스 포인트 표시용(v1.0, v1.1 등)
        - 특정 커밋에 대한 영구적이고 변경 불가능한 포인터를 생성하려는 경우

    <br>

    - **`checkout / switch / restore`**
        - checkout 기능
            - 브랜치 전환
            - 작업 디렉토리의 파일 내용 복구
            - switch, restore 가 직관적이고 단순하게 하기 위해 생김
        - git switch
            - <브랜치 이름>
                - git checkout <브랜치 이름> 과 동일
                - 현재 브랜치를 변경

            - -c <브랜치 이름>
                - git checkout -b <브랜치 이름> 과 동일
                - 새로운 브랜치를 만들고 해당 브랜치로 변경
        - git restore
            - 파일 내용 복구

> Q. tag / restore / switch 주의할 점 ?

- 항상 안정적이고 잘 테스트된 커밋에 태그를 생성 <br>
왜냐하면 커밋은 특정 시점의 프로젝트에 대한 불변의 스냅샷을 의미

- 브랜치를 전환할 때는 주의<br> 작업 손실을 방지하려면 변경 사항을 커밋하거나 숨겼는지 확인

- 작업 디렉토리에서 커밋되지 않은 변경 사항을 실수로 덮어쓰는 것을 방지하려면 주의해서 'git restore'를 사용