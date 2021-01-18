## Spring AOP

중복되는 기능(코드)를 따로 분리하여 구현하고, 이를 재조합하는 방법으로 객체지향 프로그래밍에서 발달된 형태이다.

### 프록시 패턴

Spring AOP는 프록시 패턴으로 AOP 효과를 구현한다.
어떤 클래스가 Spring AOP의 대상이라면, 클래스가 빈으로 등록되기 전에 Spring AOP가 원본 클래스에 기능을 추가한 프록시 객체를 원본 대신에 빈으로 등록한다.
Spring AOP 클래스는 어떤 타겟에 기능을 추가할지, 언제까지 유지할지, 원본 기능을 기준으로 어디에 삽입할지 등을 정의한다. 

### Spring 프록시 패턴 방법

- JDK Dynamic Proxy<br/>
자바 리플렉션 API가 제공하는 `java.lang.reflect.Proxy`를 이용하여 프록시 객체를 생성한다.
해당 클래스의 인터페이스를 기반으로 프록시 객체를 생성하기 때문에 인터페이스에 정의되어있지 않은 메소드에 대해 AOP가 적용되지 않는다.
인터페이스가 없는 클래스의 경우 프록시 객체를 생성할 수 없다.


- CGLIB<br/>
인터페이스가 없는 경우 Spring이 사용하는 방법이다. 해당 클래스를 상속받아 프록시 객체를 생성한다. 따라서 클래스가 `final`인 경우에 프록시 객체를 생성할 수 없다. 

### Filter, Interceptor, AOP 비교

Spring에서 공통 로직을 처리할 수 있는 기능은 `Filter`, `Interceptor`, `AOP`로 세 가지이다.
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile22.uf.tistory.com%2Fimage%2F9983FB455BB4E5D30C7E10)

- Filter 
  - 요청과 응답을 거른뒤 정제하는 역할을 한다.
  - 필터는 스프링 컨텍스트 외부에 존재하여 스프링과 무관한 자원에 대해 동작한다.
  - ex) 인코딩 변환 처리, XSS방어 등의 요청에 대한 처리로 사용


- Interceptor
    - `Spring`의 `Dispatcher Servelet`과 `Controller` 사이에 위치하여 `Spring`의 모든 `Bean`에 접근할 수 있다.
    - ex) 로그인 체크, 권한체크, 프로그램 실행시간 계산작업 로그확인`


- AOP
    - 메소드의 앞, 뒤 등 자유롭게 사용된다. 이를 매개변수로 지정할 수 있다.
    - 주로 '로깅', '트랜잭션', '에러 처리'등 비즈니스단의 메서드에서 조금 더 세밀하게 조정하고 싶을 때 사용한다.


### 참고

[스프링 AOP 개념 이해 및 적용 방법](https://atoz-develop.tistory.com/entry/Spring-%EC%8A%A4%ED%94%84%EB%A7%81-AOP-%EA%B0%9C%EB%85%90-%EC%9D%B4%ED%95%B4-%EB%B0%8F-%EC%A0%81%EC%9A%A9-%EB%B0%A9%EB%B2%95?category=843283)
[Spring-AOP, Proxy 란?](https://blog.naver.com/boss489/221679232206)
[Filter, Interceptor, AOP 차이 및 정리](https://goddaehee.tistory.com/154)