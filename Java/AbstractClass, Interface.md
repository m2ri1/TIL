## AbstractClass(추상클래스), Interface

### AbstractClass 란?

```
클래스 내의 *일부메서드*가 선언만 되어있고, 구현되어있지 않은 상태인 클래스
```

- abstract 키워드를 사용하여 추상클래스, 메서드를 정의한다

- 추상클래스는 기본 클래스와 마찬가지로 필드와 메서드들을 가지고, 추상메서드를 필수적으로 한 개 이상 가진다

- 자식 클래스에서 추상 클래스를 상속받아 추상메서드를 오버라이딩하여 요구사항에 맞게 사용할 수 있게 한다
  > 각각의 객체에서 공통적으로 사용하는 추상클래스를 통해 정의하여 사용하는 방식이기때문에, 메서드들의 네이밍을 통일시킬 수 있는 등 개발의 효율성을 증대시킨다
- 추상클래스를 참조하는 객체를 생성시킬 수는 없다
  > 메서드의 내용이 정의되어있지 않기때문

---

### Interface 란?

```
구현되지 않은 추상 메서드와 상수만을 포함하는 것을 말함
```

> 모든 멤버들을 추상적으로 정의하기 때문에 추상클래스보다 추상화 정도가 높다고 할 수 있다
>
> > 하지만 자바 8부터는 Default Method을 사용할 수 있게 되었다

> > -> 이는 즉 인터페이스 내에서 기능을 구현하여 모든 클래스에서 재정의를 하지 않고 메서드 사용을 가능하게 하는것이다

```
// interface 키워드를 통한 인터페이스 생성
public interface InterfaceTest {
  //
    void abstractMethod();

	// default method 생성 (자바 8 이상)
    default int defaultMethod(){
    	System.out.println("default method");
    }
}
```

- interface 키워드를 이용하여 정의하고, 인터페이스는 다른 인터페이스를 상속받을 수 있다 (또한 다중상속이 가능하다)

- 인터페이스를 상속받아 메서드의 구현을 강제하여 여러 클래스간의 설계의 표준화를 유도할 수 있는것이 장점이다

- 구현체에서는 implements 키워드를 사용하여 인터페이스를 구현한다

#### 스프링에서 인터페이스를 사용할 때의 이점

- 인터페이스를 사용하는 객체의 주요 기능과 역할을 명확하게 정의하기때문에 코드의 이해도를 높인다

- 객체가 해당 인터페이스에 의존하도록 설계를 하면 `코드간의 결합도를 낮추고`, 객체들의 `목적과 역할을 더 쉽게 파악`할 수 있다

- 다른 구현체로 쉽게 교체될 수 있기때문에 `코드 수정에 유리`한 설계를 할 수 있다

- 새로운 기능을 필요로 할 때 인터페이스를 수정함으로써 이를 구현하는 `모든 클래스에 새로운 기능을 부여`할 수 있다

---

### 인터페이스와 추상클래스의 비교

인터페이스와 추상메서드는 크게보면 비슷한 면이 있지만, 핵심적인 차이 여러가지가 있다

#### 공통점

- 메서드 내용에 대해 `선언부`만 가지고있으며, 그에 대한 `구현이 없다`

- 여러곳에서 사용되는 `공통적인 부분`을 묶어두고 그것을 각각 `구현하게 하기 위한 목적`으로 사용된다

- 독립적으로 객체를 생성할 수 없다

- 인터페이스와 추상클래스 자체의 접근제어자는 `public 또는 default` 두가지중 하나를 사용한다

#### 차이점

**_추상클래스_**

- 다양한 접근제어자를 사용하여 멤버 변수나 메서드에 대한 접근 범위를 설정할 수 있다. 단, 추상메서드는 자식 클래스에서 접근이 가능해야 오버라이딩이 가능하기때문에 `private` 접근제어자는 사용이 불가능하다

  > `public` 어떤 클래스에서든지 접근 가능

  > `protected` 같은 패키지 내의 클래스, 또는 클래스를 상속받은 다른 패키지의 클래스에서 접근 가능

  > `default` 같은 패키지 내의 클래스에서만 접근 가능  
  > (접근 제어자를 명시하지 않은 경우)

  > `private` 해당 클래스내에서만 접근 가능

- 자식에서 상속받아 사용하는 경우에 생성자를 사용할 수 있다

- 다중 상속이 불가능하다

**추상클래스 사용 예제**

```
public abstract class Animal {
    public String name;

    public Animal(String name) {
        this.name = name;
    }
    public void sleep() {
        System.out.println("동물은 잠을 잔다");
    }
    // 추상메서드 선언
    public abstract void bark();

    protected abstract void eat();

}
```

**_인터페이스_**

- 멤버변수와 메서드에는 접근제어자중 `public`만을 사용할 수 있다

- 생성자를 사용할 수 없다 (상수만을 가지기 때문에 사용할 경우가 없다)

- 다중 상속이 가능하다

**인터페이스 사용 예제**

```
public interface Interface {
    // 멤버변수는 항상 명시적으로 public static final 으로 선언된다
    int MAX_AGE = 100;

    // 디폴트메서드가 아닌 경우, 항상 명시적으로 abstract 으로 선언된다
    void move();

    // 기본적인 기능을 구현하는 디폴트메서드
    default void breathe() {
        System.out.println("동물은 숨을 쉰다");
    }
}
```

---

비슷한 기능을 하는 추상클래스와 인터페이스 중 어느것을 사용할것인가에 대한 해답으로는, 다중상속의 필요 여부로 판단할 수 있을것이다

#### 다중상속이 필요한 경우

- 객체가 여러 특성과 기능을 동시에 갖춰야 할 때

-> 각 특성을 별도의 인터페이스로 분리하여 다중상속을 받아 사용

#### 단일상속이 필요한 경우

- 객체들 사이의 명확한 계층 구조가 있을 때
- 자식 클래스가 부모의 로직을 그대로 이어받아 사용해야 할 때

-> 추상클래스 사용