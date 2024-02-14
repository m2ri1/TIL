## Spring Filter, Interceptor

Spring에서 동시에 여러 요청에 대한 공통적으로 처리해야하는 로직을 간편하게 구성할 수 있도록 하는 것입니다

- Filter란
- Interceptor란
- Filter, Interceptor의 차이 및 용도

## Filter 란

- J2EE 표준 스펙 기능으로, 자바에서 제공하는 기능입니다
- Spring의 디스패처 서블릿보다 먼저 호출되므로, Filter는 Spring범위의 밖에서 처리되는 것 입니다
- 웹 서블릿 컨테이너에 의해 관리됩니다
- 주로 인증과 관련된 로직들을 처리합니다
- bean으로 등록이 가능합니다

Spring에서 Filter를 구현하기 위해서는, `Filter` interface를 구현해야 하며
해당 인터페이스는 다음과 같은 메서드를 가지고 있습니다

#### init

객체를 초기화하고 애플리케이션에 추가하기 위한 메서드로, 초기화 이후부터는 호출되지 않음

#### dofilter

모든 요청이 디스패처 서블릿으로 전달되기 전 filter에 의해 실행되는 메소드,
`FilterChain` 에 의해 다음 대상으로 요청을 전달하게 됨

#### destory

필터 객체를 서비스에서 제거하는 메서드

> 추가적으로 OncePerRequestFilter란, 요청 처리 과정에서 Filter chain에 의해 Filter가 두번 실행되는 경우가 생길 수 있는데, 이를 방지하기 위해서 **사용자의 요청에 딱 한번만 실행되도록** 하는 필터입니다. 이름과 그대로 모든 서블릿에 일관된 요청을 처리할 수 있도록 합니다

---

## Interceptor 란

- Spring의 디스패처 서블릿이 실행되고난 후, 컨트롤러의 핸들러 실행 전(후) 요청(응답)을 가공할 수 있게합니다
- 컨트롤러의 실행 전 추가적인 작업을 원할 때 사용할 수 있습니다

Filter와 마찬가지로 인터셉터 또한 **HandlerInterceptor** 인터페이스를 구현하여 사용할 수 있고, 다음과 같은 3가지의 메서드를 가지고있습니다

#### preHandle()

컨트롤러의 호출 전 실행되어 처리되는 메서드
boolean값으로 리턴을 하는데, 이때 true가 반환될 경우 정상적으로 나머지 로직을 수행하지만 false가 반환된경우 작업을 중단시킴

#### postHandle()

preHandle의 반환값이 참 일때만 수행되는 메서드로, View가 생성되기 이전에 호출됨

#### afterCompletion()

View를 포함한 요청에 대한 최종결과를 생성하는 일이 완료된 후 실행됨
리소스를 반환해주는 등의 작업을 하기에 적절한 메서드

이 때 postHandle, afterComplection 메서드는 비동기적 요청 처리시에는 호출되지 않는 특징이 있습니다

---

## Filter, Interceptor의 차이 및 용도

#### Filter

- 서블릿 컨테이너에 의해 관리됩니다
- request, response 객체의 조작이 가능합니다
- Spring과 분리되어야 하는 기능에 사용됩니다
  > 시큐리티 인증/인가, 이미지/데이터 압축 등

#### Interceptor

- spring 컨테이너에 의해 관리됩니다
- spring에서 처리하는 내용들에 적용을 받을 수 없습니다
- 요청받은 데이터의 가공을 하는데에 있어서 사용됩니다
