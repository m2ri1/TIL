## JVM 이란

JAVA Virtual Machine의 약자로, 자바 바이트코드를 실행시킬 수 있는 주체입니다
자바의 바이트코드는 모든 운영체제에 독립적으로, JVM을 통해 어느 실행 환경에서나 자바 애플리케이션을 동일하게 수행할 수 있다는 특징이 있습니다

> `.java`파일이 기계어 `.class` 라는 java bytecode로 컴파일 되는 과정을 거친 후, JVM을 거쳐 OS에 도달하게 됩니다

## JVM의 메모리 구조

즉 Java 응용프로그램의 실행 과정입니다

### Class Loader

자바에서 소스를 작성하면 `.java` 파일이 생성되고, 해당 파일들이 컴파일러에 의해 컴파일되면 `.class` 파일이 생성됩니다
이렇게 생성된 `.class`파일들은 OS로부터 할당받은 메모리영역에 로딩되는데, 그 메모리 영역을 **Runtime Data Area** 라고 합니다
그리고 `.class` 파일을 메모리영역에 로딩하는 주체를 **Class Loader**라고 합니다

### Execution Engine

Runtime Data Area에 로딩된 `.class`파일들은 기계어로 변경되어 명령어 단위로 실행되는데, 이때 Load 된 바이트코드를 실행하는 Runtime Module이 Execution Engine입니다
Execution Engine이 실행하는데에 사용되는 방식은 두가지가 있는데,
각각의 특징과 성능을 고려하여 Interpreter 방식 또는 Just-In-Time 방식을 혼합하여 사용됩니다

- **Interpreter** 방식
  바이트코드를 한 줄씩 해석하고 실행하는 방식
- **JIT(Just In Time)** 방식
  바이트코드가 프로그램 실행시점에 맞춰 각 OS에 맞는 native code로 변환하여 속도를 개선하여 실행하는 방식

  바이트코드를 native code로 변환하는 것 또한 비용이 소모되지만, Interpreter 방식의 속도가 느리다는 문제를 개선할 수 있습니다

### Garbage Collector(GC)

Garbage란 프로그램에서 더이상 참조되지 않거나, 사용되지 않는 유효하지 않은 메모리를 말합니다
객체는 대부분 일회성으로 이용되고, 메모리에 오랫동안 남아있는 경우는 드물기 때문에 메모리누수를 방지하기 위하여 Heap메모리 영역에 적재된 객체들 중 사용되지 않는 메모리를 탐색하고, 제거하는 역할을 하는것이 Garbage Collector 입니다

#### Minor GC와 Major GC

각 객체마다 생존기간과 소모하는 메모리가 다르기때문에 효율적인 관리를 위하여 Garbage Collector는 Heap영역을 두가지로 나누어 각각의 가비지컬렉션으로 관리합니다

- Young 영역과 Minor GC
- Old 영역과 Major GC

#### Minor GC

Young 영역이란
새롭게 생성된 수명이 짧은 객체들을 할당하는 영역을 말합니다

대부분 생성된 객체는 금방 **Unreachable** 상태(접근 불가능한 상태)가 됩니다. 이는 곧 많은 객체들이 생성된 후 금방 사용되지 않는다는 의미로, 이의 효율적인 관리를 위해 새로 생성된 객체들을 Young 영역에 할당하여 **Minor GC**에 의해 관리합니다

#### Major GC

Old 영역이란
Young 영역에서 생성되었지만, **Reachable** 상태를 유지하여 계속 살아남은 객체가 복사되어 이동하는 메모리 영역입니다
즉 큰 공간을 필요로 하는 큰 객체들을 보관하는 영역이므로, Young 영역보다 큰 공간을 가지고있고, Major GC에 의해 관리됩니다

#### GC의 동작방식

- **Stop The World**
- **Mark and Sweep**

GC의 특징으로는 동작을 수행하는 동안 GC를 수행하는 쓰레드가 아닌 다른 모든 쓰레드가 일시 정지된다는 특징이 있는데, 가비지 컬렉션을 실행하기 위해 JVM이 애플리케이션의 실행을 멈추는 작업을 **Stop The World**라고 합니다

앞선 단계를 통해 모든 작업들을 중단시키고 나면, 모든 Reachable객체를 스캔하면서 각각 사용하고있는 메모리를 식별하며 **Mark** 하는데, 해당 작업을 마친 후 Mark가 되지 않은 객체들을 메모리에서 제거하게되고, 이러한 과정을 **Sweep**라고 합니다

> 위의 공통적인 단계를 따르지만, Young 영역과 Old 영역은 서로 다른 메모리 구조로 되어 있기 때문에 세부적인 동작 방식은 다릅니다

### Runtime Data Area

자바 애플리케이션을 실행할 때 사용되는 데이터들을 구분에 따라 영역을 나누어 적재하는 메모리 영역으로, 다음과 같이 분류할 수 있습니다

- Method Area
- Heap Area
- Stack Area
- PC Register
- Native Method Stack

또한 Runtime Data Area는 메모리 관리 및 프로그램 실행을 담당하는 JVM의 일부로 간주됩니다
