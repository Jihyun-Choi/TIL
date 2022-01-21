# Django

### 장고란 무엇인가요?

Django는 **파이썬 기반**(파이썬으로 만들어진) **웹프레임워크**입니다.

프레임워크란 “애플리케이션 개발에 바탕이 되는 템플릿과 같은 역활을 하는 클래스들과 인터페이스의 집합”입니다. 즉, 웹을 개발하기 위해 필요한 것들을 보다 쉽고 빠르게 개발할 수 있도록 만들어놓은 것입니다.

웹사이트를 개발 시 비슷한 유형의 요소들이 항상 필요합니다. 회원가입, 로그인, 로그아웃 등등 반복적인 작업이 필요한 것들을 하나하나 구현할 필요 없이 바로 사용할 수 있는 구성요소로 만들었습니다.

<br/>
<br/>

### APP 어떤 기준으로 분리하나요? 

한마디로 설명하자면, **앱은 재사용성을 고려해서 모델의 가장작은 단위로 분리!**

<br/>
<br/>

Django에서 APP이 어떤 기준으로 분리하는지 알아보기전에 Django에서 App이란 무엇인지 알아보자.

#### Django App이란?

Django App은 **Django에서 사용하는 "파이썬 패키지"**로 ****모듈화된 단위 프로그램이다.

- App은 MTV패턴으로 구성되며  **하나의 Django 프로젝트는 하나 이상의 Django App으로 구성**되어 있다.
- **규모가 큰 Django 프로젝트**는 보통 **여러 개의 Django App들을 모듈화**하여 구성한다. 모듈화된 App들로 구성하면 개발 및 유지 보수가 효율적으로 할 수 있다. 잘 모듈화된 App은 여러 웹 프로젝트에서 쉽게 재사용할 수도 있다.

### Django APP **기본 디렉토리 및 파일 구조**

앱 디렉토리 안에 기본 생성 파일은 다음과 같다.

```
defaultapp/
		#기본적으로 생성되는 파일
    __init__.py
    admin.py
    apps.py
    migrations/
    models.py
    tests.py
    views.py

		#추가로 넣을 수 있는 파일
		urls.py
    forms.py
    behaviors.py
    constants.py
    decorators.py
    db/
    fields.py
    factories.py
    helpers.py
    managers.py
    signals.py
    viewmixins.py
```

추가로 넣을 수 있는 파일에 대한 설명은 다음과 같다.

- [urls.py](http://urls.py) : 앱의 URL 패턴 선언
- [forms.py](http://forms.py) : 입력 폼 선언
- [behaviors.py](http://behaviors.py) : 모델 믹스인 위치에 대한 옵션
- [constants.py](http://constants.py) : 앱에 쓰이는 상수 선언
- [decorators.py](http://decorators.py) : 데코레이터
- db/ : 여러 프로젝트에서 용되는 커스텀 모델이나 컴포넌트
- [fields.py](http://fields.py) : 폼 필드
- [factories.py](http://factories.py) : 테스트 데이터 팩토리 파일
- [helpers.py](http://helpers.py) : 뷰와 모델 파일을 가볍게 하기 위해 유틸리티 함수 선언
- [managers.py](http://managers.py) : models.py가 너무 커질 경우 커스텀 모델 매니저가 위치
- [signals.py](http://signals.py) : 커스텀 시그널
- [viewmixins.py](http://viewmixins.py) : 뷰 모듈과 패키지를 더 가볍게하기 위해 뷰 믹스인을 이 모듈로 이전