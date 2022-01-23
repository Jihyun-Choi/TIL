# Django 기술 면접 질문

1. 장고 ORM의 원리를 설명해주세요
2. MVT는 무엇인가요?   이때 템플릿이 어떻게 구성되어있는지 설명할 수 있습니까?
3. [APP 어떤 기준으로 분리하나요?](https://github.com/Jihyun-Choi/TIL/blob/master/django/Tech%20Interview/Django.md#app-%EC%96%B4%EB%96%A4-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-%EB%B6%84%EB%A6%AC%ED%95%98%EB%82%98%EC%9A%94)
4. django model에서의 select_related and prefetch_related 동작 방식은 무엇인가요?
5. Django에서 Serializer 은 무엇인가요?
6. django에서 어떨때 inner join / outer join으로 나뉘는가요?
7. 일대다, 다대다 관계는 무엇인가요?
8. KeyError는 언제 발생하나요?
9. RESTful API가 무엇인가요?
10. 사용자의 요청이 API까지 도달하는 과정을 설명해주세요
    - 디자인 패턴이랑 연결해서 설명해주세요
11. request 요청시 동작 순서를 설명해주세요
12. 어떤 request가 Django API까지 도달하는 과정을 최대한 자세히 설명해주세요.
13. 로직 에러 핸들링 어떻게하는지 설명해주세요
14. 동기와 비동기에 대해 설명해주세요
15. Django ORM에서 지연 평가를 하곤 하는데요. 직접 구현한다면 어떻게 구현하겠습니까?
16. 장고에서 상속을 사용하는 경우는 어떤 경우이며 어떻게 사용하는지 설명해 주세요.

<br/>

### Rest
1. [REST란 무엇이고, RESTful하게 API를 디자인한다는 것은 무엇인지 설명하시오.](https://github.com/Jihyun-Choi/TIL/blob/master/django/Dev%20Summary/REST.md)
2. [REST API는 왜 필요한가요?](https://github.com/Jihyun-Choi/TIL/blob/master/django/Tech%20Interview/REST%20API.md#rest-api%EB%8A%94-%EC%99%9C-%ED%95%84%EC%9A%94%ED%95%9C%EA%B0%80%EC%9A%94)
3. [REST API의 장단점](https://github.com/Jihyun-Choi/TIL/blob/master/django/Tech%20Interview/REST%20API.md#rest-api%EC%9D%98-%EC%9E%A5%EB%8B%A8%EC%A0%90)
4. RESTful 웹 서비스에서 사용하는 프로토콜의 이름을 지정하십시오.
5. RESTful 웹 서비스와 관련하여 '주소 지정'이라는 용어를 설명하십시오.
6. RESTful 웹 서비스의 주된 기능을 설명하십시오.
7. 메시징 기술을 설명하십시오.
8. HTTP 요청 및 HTTP 응답의 핵심 구성 요소는 무엇입니까?
9. RESTful 웹 서비스와 관련하여 '무국적 상태'라는 용어를 설명하십시오.
10. '무국적'의 장단점을 입력하십시오.
11. RESTful 웹 서비스에 대한 몇 가지 중요한 제약 조건을 입력하십시오.
12. '리소스'란 무엇입니까?
13. 자원의 적절한 표현이 필요한 이유는 무엇입니까?
14. 캐싱이란 무엇입니까?
15. 캐시 제어 헤더를 설명하십시오.
16. RESTful 웹 서비스를 설계 할 때 따라야 할 모범 사례는 무엇입니까?
17. 페이로드 란 무엇입니까?
18. PUT 방식과 POST 방식의 차이점은 무엇인가요?
19. JAX-RS에 대해 어떻게 이해하십니까?
20. HTTP 상태 코드는 무엇입니까? 의미를 가지는 몇가지를 설명하십시오.
21. Framework와 Library의 차이점은 무엇인가요?
22. DRF(Django RestFramework)의 기본적인 동작 방식은?
23. ORM의 문제점 / 주의해야할 점
24. ViewSet과 View의 차이점

<br/>

### Design Pattern
1. 디자인 패턴의 개념과 종류
2. Singleton 패턴이란?
3. Strategy 패턴이란?
4. Template Method 패턴이란?
5. Factory Method 패턴이란?
6. MVC1 패턴과 MVC2 패턴이란?
7. Django에서 사용하는 디자인패턴은?

<br/>

### 그 외
1. TTD의 주요개념은 무엇인가요?
2. Array 할당메모리 다 차서 재 할당 할때 얼마만큼의 분량을 재할당 하는게 메모리 효율적인가?
3. 형상 관리 툴은 왜 사용하고, 사용해보신 툴이 있으시면 그 툴에 대해 자세히 말씀해 주세요.
4. 대규모 트래픽에 대한 대응으로 무엇이 있는지 간단하게 말씀해 주실 수 있나요(스케일 업, 다운)?
5. 자바스크립트에서 This는 몇 가지로 추론 될 수 있는가? 아는대로 말하여라.
6. 데이터베이스 정규화가 무엇이고 필요한 이유가 무엇입니까?
7. 교착상태가 무엇인지 설명해 주실 수 있으신가요
8. 적응형 웹과 반응형 웹의 차이를 설명해 주실 수 있나요?