## Spring Error Handling

Spring에서는 예외처리를 위해 다양한 방법을 제공합니다
아래에서 설명할 방법들은 그중 가장 자주 쓰이는 방법인 어노테이션 기반의 에러처리 방법입니다

- @ExceptionHandler
- @RestControllerAdvice

## @ExceptionHandler

ExceptionHandler는 @controller, @restcontroller가 적용된 클래스(bean) 내에서 발생된 예외를 잡고, 그에 따른 예외처리를 직접 정의한 메서드를 통해 처리할 수 있도록 합니다

```java
@RestController @RequestMapping("/test") public class TestController { // ... @ExceptionHandler(IllegalArgumentException.class) public String handleException() { return "error!"; } }
```

컨트롤러 내에서 예외가 발생한경우, 특정 예외에 대해 정의되어있는 메서드를 위와 같이 실행해줍니다

## @RestControllerAdvice

```java
@RestControllerAdvice public class ExceptionControllerAdvice { @ExceptionHandler(IllegalArgumentException.class) public String handleException() { return "IllegalArgumentException!"; } }
```

해당 어노테이션을 붙여 작성한 메서드는, 발생한 에러 처리를 전역적으로 할 수 있도록 합니다

`@RestControllerAdvice("org.example.controllers")`
`@RestControllerAdvice(assignableTypes = {TestController.class, HomeController.class})`
`@RestControllerAdvice(annotations = RestController.class)`
위와 같이 옵션을 이용해 특정 범위에만 적용시키는 방법도 있습니다

---

#### Spring 예외처리 예제

```java
package server.drawwang.global.exception;

import lombok.Getter;
import lombok.RequiredArgsConstructor;
import org.springframework.http.HttpStatus;

@RequiredArgsConstructor
@Getter
public enum CustomErrorCode {

    //==400==//
    THREAD_KING_ALREADY_EXISTS(HttpStatus.BAD_REQUEST, "쓰레드의 왕이 이미 지정되어 있습니다."),
    THREAD_NOT_EXPIRED(HttpStatus.BAD_REQUEST, "쓰레드가 만료되지 않았습니다."),
    THREAD_NOT_FOUND_ERROR(HttpStatus.NOT_FOUND, "쓰레드를 찾을 수 없습니다."),
    BOARD_NOT_FOUND_ERROR(HttpStatus.NOT_FOUND, "게시물을 찾을 수 없습니다.");

    private final HttpStatus statusCode;
    private final String statusMessage;
}
```

```java
package server.drawwang.global.exception;

import lombok.Getter;

@Getter
public class CustomException extends RuntimeException{
    private CustomErrorCode customErrorCode;
    private String detailMessage;

    public CustomException(CustomErrorCode customErrorCode) {
        super(customErrorCode.getStatusMessage());
        this.customErrorCode = customErrorCode;
        this.detailMessage = customErrorCode.getStatusMessage();
    }
}
```

```java
package server.drawwang.global.exception;

import lombok.*;

@Getter
@Setter
@AllArgsConstructor
@NoArgsConstructor
@Builder
public class CustomErrorResponse {
    private CustomErrorCode status;
    private String statusMessage;
}

```

```java
package server.drawwang.global.filter;

import com.fasterxml.jackson.databind.ObjectMapper;
import jakarta.servlet.*;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import lombok.extern.slf4j.Slf4j;
import org.springframework.http.MediaType;
import org.springframework.web.filter.OncePerRequestFilter;
import server.drawwang.global.exception.CustomErrorResponse;
import server.drawwang.global.exception.CustomException;

import java.io.IOException;
import java.nio.charset.StandardCharsets;

@Slf4j
public class ExceptionHandlerFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(
            HttpServletRequest request,
            HttpServletResponse response,
            FilterChain filterChain
    ) throws ServletException, IOException {
        try {
            filterChain.doFilter(request, response);
        }catch (CustomException e){
            setErrorResponse(response, e);
        }
    }

    private void setErrorResponse(
            HttpServletResponse response,
            CustomException customException
    ){
        ObjectMapper objectMapper = new ObjectMapper();
        response.setStatus(customException.getCustomErrorCode().getStatusCode().value());
        response.setContentType(MediaType.APPLICATION_JSON_VALUE);
        response.setCharacterEncoding("UTF-8");

        CustomErrorResponse customErrorResponse = CustomErrorResponse.builder()
                .status(customException.getCustomErrorCode())
                .statusMessage(customException.getDetailMessage())
                .build();
        try{
            response.getWriter().write(objectMapper.writeValueAsString(customErrorResponse));
        }catch (IOException e){
            e.printStackTrace();
        }
    }
}
```

일반적으로 자주 쓰이는 전역예외처리 방법의 예시입니다  
`CustomErrorCode`로 예외코드를 임의로 지정해주고, 예외 발생시 `CustomException`을 던져주어 에러코드 Enum의 상태메세지와 상태코드를 가져와 예외를 발생시킵니다  
이때 발생한 예외를 `CustomExceptionHandler`에서 잡아주고, `CustomErrorResponse`와 같은 반환객체를 생성한 후 예외에 대한 정보를 반환해줍니다

> `ExceptionHandlerFilter`란, `@ControllerAdvice` 관리 범위에 포함되지 않는 필터에서 발생한 예외를 처리하기 위한 것이고, 이를 추가해주기 위해 `Configuration`을 통해 `ExceptionConfig`에서 추가해준 것 입니다
