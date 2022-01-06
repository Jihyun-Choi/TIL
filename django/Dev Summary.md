# Django로 개발하기


### 프로젝트 환경 설정
1. New Project 눌러서 새로운 프로젝트 만들기.

2. 터미널에 (venv)가 켜져있는 것을 확인 후 `pip install django` 를 하여 장고를 설치.

3. 설치 후 `django-admin startproject (프로젝트명)`를 하여 새로운 프로젝트를 만듬.

4. File > Open Project 를 눌러 새로 만든 프로젝트를 열기.

5. File > Settings > Project: > Python interpreter에서 톱니바퀴 > Add > Ok > 기다리기 > Ok 
    Base interpreter 이 python으로 설정되어 있어야함!

6. 터미널에 새로 만든 가상환경이 존재하는 것을(맨앞에 (venv)적혀있음) 확인 후 `pip install django`



### url 작성틀
```python
from django.urls import path
from accountapp.views import hello_world

app_name = "accountapp"

urlpatterns = [
	path('hello_world/', hell0_world, name='hello_world') 
	# django.urls.path(route, view, kwargs=None, name=None, Pattern=)
]
```

app_name과 urlpatterns에 name을 지정해두는 것이 좋다. 그러면 추후에 `app이름:url이름`으로 작성 시 url주소를 전부 다 치지않아도 자동적으로 라우팅해줄 수 있기 때문이다.