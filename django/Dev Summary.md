# Django로 개발하기


### 프로젝트 환경 설정
1. New Project 눌러서 새로운 프로젝트 만들기.

2. 터미널에 (venv)가 켜져있는 것을 확인 후 `pip install django` 를 하여 장고를 설치.

3. 설치 후 `django-admin startproject (프로젝트명)`를 하여 새로운 프로젝트를 만듬.

4. File > Open Project 를 눌러 새로 만든 프로젝트를 열기.

5. File > Settings > Project: > Python interpreter에서 톱니바퀴 > Add > Ok > 기다리기 > Ok 
    Base interpreter 이 python으로 설정되어 있어야함!

6. 터미널에 새로 만든 가상환경이 존재하는 것을(맨앞에 (venv)적혀있음) 확인 후 `pip install django`

<br/>
<br/>

### gitignore 만들기

1. 프로젝트에 `.gitignore` 파일 생성하기

2. [https://github.com/github/gitignore/blob/main/Global/JetBrains.gitignore](https://github.com/github/gitignore/blob/main/Global/JetBrains.gitignore) 복붙해서 작성하기

3. 추가적으로 gitignore해야하는 것들을 작성하기

<br/> 

### git 활성화 시키기
파이참의 맨 위 상단의 VCS > Enable Version Control Intergration > 셀렉트박스에서 Git을 선택 > OK

<br/>
<br/> 

### SECRET_KEY 분리하기 

1. 터미널에 `pip install django-environ` 을 실행한다.

2. 프로젝트에 `.env` 파일 생성하기

3. 아래의 코드를 생성한 `.env` 파일에 복붙한다.  
    
    ```
    DEBUG=on
    SECRET_KEY= [따옴표 없이 SECRET_KEY 복붙하기]
    DATABASE_URL=psql://urser:un-githubbedpassword@127.0.0.1:8458/database
    SQLITE_URL=sqlite:///my-local-sqlite.db
    CACHE_URL=memcache://127.0.0.1:11211,127.0.0.1:11212,127.0.0.1:11213
    REDIS_URL=rediscache://127.0.0.1:6379/1?client_class=django_redis.client.DefaultClient&password=ungithubbed-secret
    ```
    
4. 아래와 같이 settings.py에 있는 코드들을 수정한다.
    
    ```python
    # settings.py 수정 전
    import environ
    
    # reading .env file
    environ.Env.read_env()
    
    SECRET_KEY = '제공된 랜덤값'
    ```
    
    ```python
    # settings.py 수정 후
    import os, environ
    
    # reading .env file
    environ.Env.read_env(
        env_file= os.path.join(BASE_DIR, '.env') # BASE_DIR를 선언한 코드 아래에 이 코드가 있어야함
    )
    
    SECRET_KEY = env('SECRET_KEY')
    ```
    
5. `.env` 파일을 `.gitignore` 에 추가한다.

<br/>
<br/>

### git clone 하기 
1. Get form Version Control 누르기

2. 복사하고자 하는 git의 URL 넣기

3. clone 누르기

<br/>
<br/>

### requirements 만들기 & 설치하기

pip freeze > requirements.txt

본인 pip list 패키지들을 텍스트문서로

pip install -r requirements.txt

pip list들을 적은 requirements에 들어있는 패키지들을 설치 → 가상환경 동일하게 셋팅

<br/>
<br/>

### App 만들기
1. python [manage.py](http://manage.py) startapp 앱이름

2. 기본앱의 settings.py의 INSTALLED_Apps에서 새로만든 앱이름 적기

3. 새로만든 앱의 view를 작성

4. 기본앱의 urls.py에서 새로운앱의url 주소 작성

5. 새로만든 앱에 [urls.py](http://urls.py) 만든 후 코드작성    
    주소, view, name(라우트에 대한 이름)           app_name작성해두면 주소작성시 좋음

```python
#기본앱 urls.py

urlpatterns = [ 
    path('admin/', admin.site.urls),
    path('accounts/', include('accountapp.urls')), 
]
```

```python
#추가앱 urls.py

from django.urls import path
from accountapp.views import hello_world

app_name = "accountapp"

urlpatterns = [
	path('hello_world/', hell0_world, name='hello_world') 
	# django.urls.path(route, view, kwargs=None, name=None, Pattern=)
]
```

app_name과 urlpatterns에 name을 지정해두는 것이 좋다. 그러면 추후에 `app이름:url이름`으로 작성 시 url주소를 전부 다 치지않아도 자동적으로 라우팅해줄 수 있기 때문이다.

<br/>
<br/>

### DB 연동하기

1. `python manage.py makemigrations`

    models.py에서 쓰는 명령어를 디비와 연동시킬 수 있는 파이썬 파일로 만들어줌
    
    *null은 디비에 저장할때 공백이어도 되는지 아닌지, FALSE이면 공백이면 안된다 !*

2.  `python manage.py migrate`

    파일만 만든다고 다 되는것이 아니다! 파일과 디비를 연동시켜줘야 된다.