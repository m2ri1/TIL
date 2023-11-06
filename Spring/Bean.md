### Bean 이란?

스프링 컨테이너(즉 ApplicationContext) 에 의해 생성, 관리되는 인스턴스화 된 객체  
주로 `@Component`, `@Service`, `@Repository`, `@Controller`와 같은 어노테이션을 통한 **컴포넌트 스캔** 방식으로 주로 빈이 생성되지만
xml 설정파일에서 직접 클래스를 빈으로 등록하고 의존성을 주입하는 방식, 또는 Java Config 파일에서 Java 코드로 빈 설정을 직접 하는 방법도 있다

```java
package com.example.api;

import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@EnableAutoConfiguration
@ComponentScan("com.example.core")
public class ApiBeanConfigure {

}
```

> BeanConfig 파일을 이용해 빈을 직접 설정해주는 예제

그리고 이렇게 생성된 빈은 필요한경우 **컨테이너에 의해 의존성 주입**을 받는다

> 인스턴스화 된 객체를 빈이라고 말하지만, new 연산자등을 통해 생성된 객체 등 스프링 애플리케이션에서 생성되는 모든 객체가 빈인것은 아니다

#### Bean의 라이프사이클

`스프링 IoC 컨테이너 생성` → `스프링 빈 생성` → `의존관계 주입` → `초기화 콜백 메소드 호출` → `사용` → `소멸 전 콜백 메소드 호출` → `종료`

이 과정에서 빈들은 Bean Scope에 의해 관리되며, 각 scope에 따라 IoC 컨테이너가 관리하는 빈의 생명 주기와 범위가 다르다
