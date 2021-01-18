## Spring PSA (Portable Service Abstraction)

추상화 계층을 사용해서 어떤 기술을 내부에 숨기고 개발자에게 편의성을 제공해주는 것을 `Service Abstraction`이라 한다.
더하여 `Service Abstraction`으로 제공되는 기술을 다른 기술 스택으로 간편하게 바꿀 수 있는 확장성을 갖고 있는 것이 `Portable Service Abstraction`이다.

### Spring Web MVC

일반 클래스에 `@Controller` 어노테이션을 사용하면, 요청을 맵핑할 수 있는 컨트롤러 클래스가 된다.
이 곳에서 `@GetMapping`, `@PostMapping`등의 어노테이션으로 요청을 맵핑할 수 있다.
이렇게 간단하게 요청을 맵핑할 수 있는 이유는 `Spring`이 뒷단의 서블릿 기능들이 숨어있기 때문이다.

`Spring Web MVC`는 톰캣 서버를 내장하고 있다. 이 의존을 `Web Flux`로 변경만 하면, 코드는 그대로여도 `netty` 기반으로 실행되게 된다.
이렇게 `PSA`는 기술을 추상화함으로써 유연성 있는 코드를 구현할 수 있다.

### 참고

- [스프링 PSA](https://atoz-develop.tistory.com/entry/Spring-%EC%8A%A4%ED%94%84%EB%A7%81-PSA?category=843283)