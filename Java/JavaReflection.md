### Java Reflection이란

class 타입이 객체 정보에서
생성자, 메서드, 필드, 클래스 등에 대한 정보를 자세히 알아낼 수 있도록 지원하는 기법(api)을 말합니다
이때 가져올 수 있는 정보들은 class 타입의 객체를 말하고, 접근제어자와 상관없이 사용할 수 있도록 한다는 특징이 있습니다

##### class 타입 객체란

자바 파일이 실행될 때 jvm에 의해 클래스파일에 대한 로딩을 완료한 후 힙 메모리에 저장된 것으로, new 키워드를 사용하여 만든 객체와는 다릅니다

리플렉션을 사용하여 가져올 수 있는 정보

- class
- constructor
- method
- field
- annotation
  등..

### Reflection을 사용하는 방법

리플렉션을 사용하기 위해서는, 힙 영역에 로드된 class 타입의 객체들을 가져와야 합니다

- 클래스명.class
- 인스턴스.getClass()
- Class.forName("클래스명)

Member라는 이름의 클래스 타입을 가져오기 위한 방법 예제

```java
//1
Class<Member> memberClass = Member.class;
//2
Class<? extends Member> memberClass2 = member.getClass();
//3
Class<?> memberClass3 = Class.forName("{패키지명}.Member");
```

다음과 같은 3가지 방법 모두 동일한 해시코드를 가진 객체를 가져오게 되고, 이 방법을 통해 얻은 Class객체를 사용하여 다양한 리플렉션 작업을 수행할 수 있습니다

> 각각 생성된 객체들은 동일한 Member 클래스를 나타내는 Class 객체를 참조하므로 동일한 해시코드를 가진다

### Reflection 사용 예제

```java
import java.lang.reflect.Method;

public class ReflectionExample {

    public static void main(String[] args) throws Exception {
        // Member 클래스의 Class 객체 가져오기
        Class<?> memberClass = Class.forName("Member");

        // Member 클래스의 인스턴스 생성
        Object memberInstance = memberClass.newInstance();

        // speak 메서드의 Method 객체 가져오기
        Method speakMethod = memberClass.getDeclaredMethod("speak", String.class);

        // speak 메서드 호출
        speakMethod.invoke(memberInstance, "안녕하세요!");
    }
}

```

```java
public class Member {

    private String name;

    public Member() {
    }

    public Member(String name) {
        this.name = name;
    }

    public void speak(String message) {
        System.out.println(name + "이(가) 말합니다: " + message);
    }
}

```

## Reflection의 특징

- 런타임 시점에서 클래스의 인스턴스 생성이 가능합니다
- 접근제어자와 관계없이 모든 필드와 메소드에 접근이 가능합니다
- 캡슐화를 저해합니다
- 리플렉션을 사용하여 접근할때의 상대적인 성능이 느립니다

객체지향 설계에 있어 중요한 캡슐화를 깨뜨릴 수 있지만, 규모가 큰 프로그램의 개발단계에서는 수많은 객체들의 의존관계를 파악하기 어렵기 때문에 리플렉션을 유용하게 사용하는 것입니다
