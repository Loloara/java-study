## Spring Bean

Spring IoC 컨테이너가 관리하는 자바 객체를 Bean 이라고 한다.

### Spring IoC 컨테이너가 빈을 등록하는 방법

- Component Scanning<br/>
`@ComponentScan` 어노테이션 포함한 클래스와 하위 패키지의 모든 클래스를 스캔하여 `@Component` 어노테이션 또는 `@Component` 어노테이션을 사용하는 다른 어노테이션이 붙은 클래스를 찾아서 빈으로 등록한다.


- 빈 설정파일에 직접 빈을 등록<br/>
자바 설정 파일을 뜻하는 `@Configuration` 어노테이션도 내부적으로 `@Component`를 사용하기 때문에 스캔의 대상이 되며 이때 클래스 내부에 `@Bean` 어노테이션으로 직접 빈을 정의할 수 있다.

### Bean Life Cycle

생성, 초기화, 사용, 소멸 이라는 Life Cycle을 가지고 있다.

#### 생성

- 컨테이너에서 빈 설정정보(Bean Configuration)를 읽는다.
- 컨테이너에서 빈 조립설명서(Bean Definition)를 생성한다.
- 컨테이너가 설정한 Bean Scope 규칙에 따라 Bean을 생성한다. (default singleton)
- singleton : 인스턴스가 있으면 사용하고, 없으면 생성하는 방식이다.

#### 초기화

- Bean 생성 이후 초기화를 수행한다.
- 초기화를 하기 위한 다양한 방법을 제공한다.
    - InitialIzingBean 인터페이스 구현
    - init-method지정 (xml or java  annotation config)
    - @PostConstruct 지정

#### 사용

- IoC Container를 통해 생성된 Bean을 지정한 Bean Scope 규칙으로 사용 (default singleton)

#### 소멸

- 컨테이너가 종료될 때 destory 메소드가 선언되어 있다면 수행
- 소멸 시 사용할 수 있는 다양한 destroy 방법이 있음
    - DisponsableBean 인터페이스 구현 (destroy() 메소드)
    - destroy-method를 지정 (xml or java annotation config)
    - @Predestory 지정

### Bean Scope

|Scope|Description|
|----|----|
|singleton|하나의 Bean 정의에 대해서 Spring IoC Container 내에 단 하나의 객체만 존재한다.|
|prototype|하나의 Bean 정의에 대해서 다수의 객체가 존재할 수 있다.|
|request|하나의 Bean 정의에 대해서 하나의 HTTP request의 생명주기 안에 단 하나의 객체만 존재한다; 즉, 각각의 HTTP request는 자신만의 객체를 가진다. Web-aware Spring ApplicationContext 안에서만 유효하다.|
|session|하나의 Bean 정의에 대해서 하나의 HTTP Session의 생명주기 안에 단 하나의 객체만 존재한다. Web-aware Spring ApplicationContext 안에서만 유효하다.|
|global session|하나의 Bean 정의에 대해서 하나의 global HTTP Session의 생명주기 안에 단 하나의 객체만 존재한다. 일반적으로 portlet context 안에서 유효하다. Web-aware Spring ApplicationContext 안에서만 유효하다.|

#### 싱글톤으로 적합한 객체

- 상태가 없는 공유 객체
- 읽기용으로만 상태를 가진 공유 객체
- 공유가 필요한 상태를 지닌 공유 객체
- 쓰기가 가능한 상태를 지니면서도 사용빈도가 매우 높은 객체

#### 비싱글톤으로 적합한 객체

- 쓰기가 가능한 상태를 지닌 객체
- 상태가 노출되지 않은 객체

### 참고

[스프링 빈(Bean)의 개념과 생성 원리](https://atoz-develop.tistory.com/entry/Spring-%EC%8A%A4%ED%94%84%EB%A7%81-%EB%B9%88Bean%EC%9D%98-%EA%B0%9C%EB%85%90%EA%B3%BC-%EC%83%9D%EC%84%B1-%EC%9B%90%EB%A6%AC)
[Bean Life Cycle](https://www.slipp.net/wiki/pages/viewpage.action?pageId=25528047)
[Bean Scope](https://www.slipp.net/wiki/pages/viewpage.action?pageId=25528177)