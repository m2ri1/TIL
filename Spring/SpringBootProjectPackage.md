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

- `api` : controller 클래스가 존재

- `application` 비즈니스 로직을 담당하는 service 클래스들로 구성

- `dao` : dao, repository 클래스들로 구성

- `domain` : entity 클래스들로 구성

- `dto` : dto 클래스들로 구성

- `exception` : exception 클래스들로 구성

`global`

- `config` : 스프링의 각종 설정을 담은 파일
- `auth` : 인증/인가에 사용되는 설정을 담은 파일
- `common` : 공통으로 사용되는 Value 객체

---

### 계층형

**스프링 웹계층을 기반으로 각 계층을 대표하는 클래스와 디렉토리로 구성되어있다**  
전체적인 구조를 빠르게 파악할 수 있다는 장점이 있지만, 각 디렉토리내에 클래스들이 너무 많아져 혼란이 생길 수 있다

```
com
 ㄴ example
     ㄴ project
         ㄴ config
         ㄴ controller
         ㄴ domain
         ㄴ repository
         ㄴ service
         ㄴ security
         ㄴ exception
```

- `config` : 스프링의 각종 설정을 담은 파일로 구성

- `controller` : 웹 요청을 처리하는 컨트롤러 클래스들로 구성

- `domain` : Entity나 DTO와 같은 도메인 모델 클래스들로 구성

- `repository` : 데이터베이스와의 연결을 담당하는 Repository 인터페이스나 클래스들로 구성

- `service` : 비즈니스 로직을 처리하는 service 클래스들로 구성

- `security` : 사용자 인증, 권한 검사와 같은 기능들을 다루는 클래스들로 구성

- `exception` : exception 클래스들로 구성
