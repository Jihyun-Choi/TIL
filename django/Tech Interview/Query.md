# model에서 select_related and prefetch_related 동작 방식

데이터베이스는 **모든 자료들이 파일의 형태로 디스크에 저장**이 된다. **파일은 일련의 블럭들의 집합으로 구성**된다. 블럭들이 메인 메모리에 저장이 되며 프로세싱을 하게되는 형태이다. 블럭이 전송되는 부분이 데이터베이스의 성능을 좌우하므로 **블럭의 수를 줄이는 것이 DB최적화**이다. 

<br/>

**쿼리란** 데이터베이스에 정보를 요청하는 것이다. 즉, 쿼리를 줄일수록 DB 최적화를 위한 성능을 향상시킬 수 있다. 또한 쿼리셋은 DB에 Access 할 때 캐시 메모리를 포함한다. 처음 쿼리셋이 연산될 때, 캐시가 비어있으므로 Query가 발생한다. 그 이후 동일한 쿼리셋을 사용할 경우 추가적인 Query는 발생하지 않고, 캐시에서 꺼내서 사용한다.

<br/>

이러한 관점에서 **select_related** 와 **prefetch_related**를 사용하면 **여러줄의 쿼리를 간단하게 만드므로 DB에 접근하는 수를 줄여 성능을 향상**시킬 수 있다. **select_related** 와 **prefetch_related**는 비록 쿼리를 복잡하게 만들지만 하나의 QuerySet을 가져올 때, 미리 related objects들까지 다 불러오므로 캐시로인해 다시 DB에 접근할 필요가 없다.

<aside>
QuerySet : 데이터베이스에서 전달 받은 모델의 객체 목록 (python data structure)

ORM(Object-relational Mapping) : DB와 객체지향 프로그래밍 언어 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법
</aside>

<br/>
<br/>

> **select_realted**
> 

---

쿼리셋을 반환할 때 **foreign-key, OneToOneFeild** 관계인 모델들 함께 가져오는 ORM

**foreign-key, OneTonOneFeild** 관계인 모델들을 코드에서 재사용할 경우 추가적인 쿼리가 필요 없습니다.

<br/>

> **prefetch_related**
> 

---

`prefetch_related()`는 foreign-key , one-to-one 뿐만 아니라 many-to-many , many-to-one 등 모든 relationships에서 사용 가능

Selected_related는 하나의 Query로 related Objects들을 불러오지만, Prefetch_related는 main query가 실행이 된 후 별도의 query가 실행이 된다. 따라서 1번 이상 쿼리가 진행되기 때문에 **가급적 selected_related**를 사용하는 것이 리소스를 줄일 수 있다.

<br/>

> **select_related** and **prefetch_related 차이**
> 

---

정참조, 역참조의 차이도 있지만 실제 Join 을 어디서 하냐의 차이가 있다.

select_related 같은경우 DB에서 Join 을 한 채로 가져오고, prefetch 는 가져와서 Python 으로 Join 을 하게 된다. 정말 간단하게는 Select는 DB에서 join 기능을 수행한 후 가져오므로 1 Query가 실행된다면 Prefetch는 python에서 join 기능을 수행하므로 불러올때 1 Query를 실행하고 불러온 후 1 Query를 한번더 실행한다. 즉, 가급적 Select_related를 사용하는것이 효율적이라 할 수 있겠다.

`prefetch_related`는 원래 main query 실행된 후 별도의 query를 따로 실행하게 된다. 반면에 `select_related` 은 하나의 query만으로 related objects들을 다 갖고오게된다.

many-to-many , many-to-one 과 같은 relationships에서는 prefetch_related 를 사용해야되지만, foreign-key , one-to-one 와 같은 single-valued relationships이 있는 곳에서는 최대한 select_related 를 사용하여 query 수를 줄여주는 것이 효과적이다.