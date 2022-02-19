# 프로세스 동기화


### 프로세스 간 통신

프로세스는 독립적으로 실행되기도 하지만 다른 프로세스와 데이터를 주고받으며 통신을 하는 경우가 있다. 

한 컴퓨터 내에 실행되고 있는 다른 프로세스, 또는 네트워크로 연결된 다른 컴퓨터에 있는 프로세스와 통신할 수 있다. 

<br/>

**프로세스 간 통신의 종류**

한 컴퓨터 내에서 프로세스 간 통신을 하는 방법 : 파일과 파이프를 이용

    파일을 이용 : 통신하려는 프로세스들이 하나의 파일을 읽고 쓰는 방법
    파이프 이용 : 운영체제가 생성한 파이프를 이용해 데이터를 읽고 쓰는 방법

쓰레드 이용 : 한 프로세스 내에서 쓰레드 간 통신을 하는 방법

    (쓰레드 - 코드, 데이터, 힙 영역을 공유, 스택만 자신의 것으로 보유)

네트워크를 이용한 방법

    운영체제가 제공하는 소켓통신
    다른 컴퓨터에 있는 함수를 호출하는 RPC(원격 프로시저 호출)를 이용해 통신

<br/>
<br/>

### 공유자원과 임계구역

공유자원 : 프로세스 간 통신을 할 때 공동으로 이용하는 변수, 파일 

공유자원은 여러 프로세스가 공유하고있으므로 각 프로세스의 접근 순서에 따라 결과가 달라질 수 있다. ← 문제점

컨텍스트 스위칭으로 시분할 처리를 하므로 어떤 프로세스가 먼저 실행되고 어떤 프로세스가 나중에 실행되는지 예측하기가 힘들다. 

따라서 연산결과를 예측하기 어렵고, 여기서 발생한 문제를 “동기화 문제” 라고 부른다.

예시 → 게임 물약 먹기 & 공격당함 동시 처리시 발생하는 문제점
    
임계구역(Critical Section) : 여러 프로세스가 동시에 사용하면 안되는 영역을 정의

경쟁조건 : 공유자원을 서로 사용하기 위해 경쟁하는 것

임계구역에서 발생하는 문제를 해결하기 위한 기법은 다음에!


문제를 해결하기 위해서는 상호 배제(Mutual Exclusion) 메커니즘이 필요하다.

상호 배제의 요구사항 : 3가지

1. 임계영역엔 동시에 하나의 프로세스만 접근
2. 여러 요청에도 하나의 프로세스의 접근만 허용
3. 임계구역에 들어간 프로세스는 빠르게 나와야함

<br/>
<br/>

### 세마포어

상호배제 메커니즘의 한 가지인 세마포어에 대해 알아보자. 동기화에서 가장 중요한 개념!!! 

예시 : 2명이서 네트워크로 공유된 프린터를 통해 인쇄해보자!

프린터를 사용하려던 직원들 : 프로세스

프린터 - 여러 프로세스들이 같이 쓰고있는 : 공유자원

프린터를 쓰기위해 프로세스가 기다리는 공간 : 대기큐

열쇠관리자 : 운영체제

열쇠관리자가 가지고있는 열쇠 : 세마포어!!!!  (정수형 변수)

이제 세마포어를 코드로 어떻게 쓰는지 알아보자!

```python
int s = 1;  // 세마포어 선언

wait(s); // 열쇠를 요청해서 열쇠를 받고 문을 잠금
실행코드
signal(s);  // 방에서 나와 문지키는 직원에게 열쇠 반납
```

세마포어 이용시 공유자원에 여러 프로세스가 동시에 접근하지 못하기 때문에 동기화 문제가 발생하지 않는다. 

예시에선 열쇠가 1개인 세마포어로 설명했지만, 세마포어는 실제로 여러개의 열쇠를 가질 수 있다. 

세마포어가 정수형 변수이므로 공유자원이 2개라면 세마포어의 값은 2로 설정하면 된다.

단점

wait() 함수와 signal() 함수의 순서를 이상하게 호출 시 세마포어를 잘못 사용할 가능성이 존재

이를 해결하고자 “모니터”라는 방법이 존재

<br/>
<br/>

### 모니터

모니터 : 세마포어의 단점을 해결한 상호배제 메커니즘

모니터는 따로 운영체제가 처리하는 것이 아닌 프로그래밍 언어 차원에서 지원하는 방법

대표적으로 자바에서 모니터를 지원

```java
public class Health {
	private int health = 100;

	synchronized void increase(int amount){
		health += amount;
	}
	synchronized void decrease(int amount){
		health -= amount;
	}
}
```

`synchronized` 키워드가 붙으면 이 키워드가 붙은 함수들은 동시에 여러 프로세스에서 실행시킬 수 없다. 즉, 상호배제가 완벽하게 이루어진다. 

모니터의 구현만 완벽하다면 프로그래머는 세마포어처럼 wait() 함수나 signal() 함수를 임계영역에 감싸지 않아도돼서 편리하고 안전하게 코드를 작성할 수 있다.
