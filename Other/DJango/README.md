# DJango 장고

<br>
<br>

> 설치 방법

- `poetry 로 가상환경 설정`
```
mkdir backend-db

cd backend-db

poetry init

code .
```

- `poetry 가상환경에 DJango 설치`
```
poetry add Django
```

- `poetry 가상환경에 DJango 실행`
```
poetry shell
```

- `DJango 프로젝트 생성`
```
django-admin startproject config .
```

- `migrate 하기`
```
python manage.py migrate
```

- `DJango 서버 실행`
```
python manage.py runserver
    or
django-admin runserver
```

- `admin 계정 생성`
```
python manage.py createsuperuser
```
