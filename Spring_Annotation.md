## Spring Annotation 정리

### Spring에서 Annotation 이란?

- 소스코드에 추가하여 클래스와 메소드에 특별한 기능을 부여할 수 있도록 하는 역할

- 코드량의 감소, 유지보수성 향상

- 생산성의 증가

---

### @Controller

해당 클래스가 컨트롤러의 역할을 한다는것을 명시

```
@Controller
// 해당 Class는 Controller 역할을 함

@RequestMapping("/user")
// /user로 들어오는 요청을 모두 처리

public class UserController {
    @RequestMapping(method = RequestMethod.GET)
    public String getUser(Model model) {
    //  GET method, /user 요청을 처리
    }
}
```

### @GetMapping

요청 들어온 URI의 요청과 Annotation value 값이 일치하면 해당 클래스나 메소드를 실행

_RequestMapping(Method=RequestMethod.GET) 과 같은 역할_

```
@Controller
@RequestMapping("/user")

public class UserController {

    @GetMapping("/")
    public String getUser(Model model) {
    //  GET method, /user 요청을 처리
    }

    @RequestMapping(method = RequestMethod.GET)

    public String getUser(Model model) {
    //  GET method, /user 요청을 처리
    }
}
```

### @PostMapping

_RequestMapping(Method=RequestMethod.POST)과 같은 역할_

```
@Controller
@RequestMapping("/user")

public class UserController {
    @RequestMapping(method = RequestMethod.POST)
    public String addUser(Model model) {
        //  POST method, /user 요청을 처리
    }

    @PostMapping('/')
    public String addUser(Model model) {
        //  POST method, /user 요청을 처리
    }
}
```

### @SpringBootTest

Spring Boot Test에 필요한 의존성 제공

### @Component

Class를 Spring의 Bean으로 등록할 때 사용

### @RequestParam

URL에 전달되는 파라미터를 메소드의 인자와 매칭시켜 처리
