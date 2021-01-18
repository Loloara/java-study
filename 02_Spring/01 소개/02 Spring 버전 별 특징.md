## Spring 버전별 특징

### Spring 3.2.X

- `Java 5`의 기능 (제네릭, 가변 매개변수 등)을 사용하여 개정되었다.
- `@Async` 주석을 통해 비동기 메서드 호출을 지원하기 시작했다.
- 하나의 `Spring.jar`로 제공하던 것을 여러 `Spring` 모듈의 `jar` 파일로 나누어 제공하기 시작했다.<br/>
  (ex : `spring-core`, `spring-web` 등)
- `SPEL(Spring Expression Language)` 가 도입되어 `XML` 및 `Annotation` 기반 `Bean`정의에서 사용할 수 있게 되었다.
  - 이로 인해서 외부 프로퍼티 파일이나 환경변수에서 값을 가져오기 쉬워졌다.
- `Java` 클래스로부터 `@Configuration`, `@Bean` 등의 `Annotation`을 사용해서 직접 메타 데이터를 설정하고, DI 지원을 받을 수 있다. 
- `OXM(Object Xml Mapping)`을 사용하여 `Bean`을 `XML`형태로 관리할 수 있게 되었다.
- Rest API 에 대한 지원이 추가되었다.
  - 서버로서는 기존 `MVC Framework` 레벨에서 `Annotation` 기반 확장이 추가되었다.
  - 클라이언트로서는 `RestTemplate` 을 추가해 지원한다.
- `H2`등의 `Embeded Database`를 지원한다.
- 2016년 12월 31일부로 개발 및 지원이 종료되었다.

### Spring 4.3.X

- `Java 8`의 기능을 완전히 지원하기 시작했다.
- `Starter Pack`의 등장으로 초기 설정이 보다 용이해졌다.
- `Groovy` 를 통한 `Bean` 설정이 가능하다.
- `Core Container` 들의 기능 지원이 확대되었다.
  - 예를 들어, `Spring Data Repository` 를 사용하고 있다면 간단한 구현으로 주입할 수 있다.<br/>
    (`@Autowired Repository<Customer> customerRepository`)
  - `meta-annotation` 지원과 함께 `custom-annotation` 을 만들 수 있다.
  - `Bean` 관리가 더 용이해졌다.
    - `@Order` 어노테이션을 통해 배열과 리스트 형태의 `Bean`을 정렬 할 수 있다.
    - `@Lazy` 어노테이션을 통해 `Lazy Injection`이 가능하다.
- `@RestController` 등 `Web` 개발 도구의 지원이 강화되었다.
- `WebSocket`이나 `STOMP` 등의 프로토콜을 지원하여 양방향 통신이 가능하다.
- 테스트 환경이 개선되어 `Framework` 레벨에서 테스트 유틸리티를 지원한다.
- (ex. `AopTestUtils`, `ReflectionTestUtils(개선)`)
- 2020년 12월 31일부로 개발 및 지원이 종료되었다.

### Spring 5.X

- `Java 8` 버전이 기본으로 설정
- `JDK 9`와 완벽 호환된다.
- `Jackson 2.9`, `Protobuf 3`, `Reactor 3.1`과의 호환 추가
- `Spring WebFlux` 추가, 비동기와 넌-블로킹 이벤트 루프 모델 사용 가능
- `Kotlin` 지원
- `Junit 5` 지원
- `5.0.x` 버전은 2020년 10월까지 지원되며, `5.1.x` 버전과 `5.2.x` 버전은 각각 2020년 10월, 2021년 말까지 활발히 개발될 것이다. `5.3.x` 버전은 알파버전으로, 2024년까지 지원이 제공된다.

### 참고
- [Spring의 버전 별 차이](https://m.blog.naver.com/whdgml1996/222001483936)
- [Spring 버전 별 특징](https://velog.io/@hygoogi/%EC%8A%A4%ED%94%84%EB%A7%81-%EB%B2%84%EC%A0%84-%EB%B3%84-%ED%8A%B9%EC%A7%95)