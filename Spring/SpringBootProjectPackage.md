## SpringBoot 프로젝트 패키지 구조

### 도메인형

**프로젝트의 도메인형 디렉토리 구조는, 스프링 웹 계층에 주목하기보다는 도메인에 주목하여 설계한다**  
각 도메인별로 패키지를 분리하여 계층형 방식보다 패키지관리에 수월하다  
또한, 각각의 도메인끼리 서로 의존하지 않도록 설계한다

```
com
 ㄴ example
     ㄴ vivid
         ㄴ domain
         |   ㄴ user
         |   |   ㄴ api
         |   |   ㄴ application
         |   |   ㄴ dao
         |   |   ㄴ domain
         |   |   ㄴ dto
         |   |   ㄴ exception
         |   ...
         ㄴ global
             ㄴ auth
             ㄴ common
             ㄴ config
             ㄴ error
             ㄴ infra
             ㄴ util
```

`domain`
domian과 entitiy를 기준으로 하위 패키지를 구성

- `api` : controller 클래스가 존재합니다

- `application` 비즈니스 로직을 담당하는 service 클래스들로 구성

- `dao` : dao, repository 클래스들로 구성

- `domain` : entity 클래스들로 구성

- `dto` : dto 클래스들로 구성

- `exception` : exception 클래스들로 구성

`global`

- `config` 스프링의 각종 설정을 담은 파일
- `auth` 인증/인가에 사용되는 설정을 담은 파일
- `common` 공통으로 사용되는 Value 객체
