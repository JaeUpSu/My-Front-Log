<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `ReactDjango Linking of MyInfo Project`

<br>


* **설명**
* **구현**
* **전체**

<br>


> 설명

```
Front & Back 연결

Front 파일을 npm run build 가 
python manage.py runserver react 로 
실행 가능하게 하여 연결
```

<br>
<br>

> 구현

<br>

### &nbsp;&nbsp;`* Back`


### &nbsp; *manage.py*<br>
&nbsp; - python manage.py runserver 할 때
```python
try:
    if sys.argv[2] == 'react':
        project_root = os.getcwd()
        os.chdir(os.path.join(project_root, "my-info-web"))
        os.system("npm run build")
        os.chdir(project_root)
        sys.argv.pop(2)
```
<br>



> 전체

<br>

### &nbsp; *manage.py*<br>
```python
import os
import sys

def main():
    """Run administrative tasks."""
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "config.settings")
    try:
        from django.core.management import execute_from_command_line
    except ImportError as exc:
        raise ImportError(
            "Couldn't import Django. Are you sure it's installed and "
            "available on your PYTHONPATH environment variable? Did you "
            "forget to activate a virtual environment?"
        ) from exc
        
    try:
        if sys.argv[2] == 'react':
            project_root = os.getcwd()
            os.chdir(os.path.join(project_root, "my-info-web"))
            os.system("npm run build")
            os.chdir(project_root)
            sys.argv.pop(2)
    except IndexError:
        execute_from_command_line(sys.argv)
    else:
        execute_from_command_line(sys.argv)


if __name__ == "__main__":
    main()
```
<br>


