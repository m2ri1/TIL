## Spring DI (Dependency Injetction, 의존성 주입)

의존성 주입이란?

```
어떤 객체가 사용하는 의존객체를 직접 만들어 사용하는게 아니라, 외부로부터 주입받아 사용하는 방법
(new 연산자를 이용해서 객체를 생성하는 것 대신 스프링 컨테이너에서 객체를 생성하는 방식)
```

- _의존성 주입을 통해서 모듈 간의 결합도가 낮아지고 유연성이 높아진다는 장점이 있다_

---

### Spring에서의 의존성 주입 방법

- 생성자 주입

> @Autowired를 붙여 생성자에 의존성을 주입받을 수 있다

- 필드 주입
- 수정자 주입(setter)

-> Spring에서는 생성자 주입을 사용하는것을 권장하는데, 그 이유는 다음과 같다

- 객체 불변성 확보
- 테스트에 용이
- 순환참조 에러방지