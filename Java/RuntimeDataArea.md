## Runtime Data Area 란

JVM이 프로그램을 수행하기 위해 OS로부터 할당받는 메모리 영역을 말하고, 다음과 같이 5가지로 구분됩니다

Thread별로 생성되는 영역

- PC Register
- JVM stack
- Native Method stack

모든 Thread가 공유하는 영역

- Heap
- Method Area

#### PC Register

- 현재 수행중인 JVM 명령의 주소를 저장하는 공간
- Thread가 어떤 명령을 실행하게 될지에 대한 부분을 기록
- Stack에서 Operand(명령)를 뽑아내어 저장

#### JVM Stack

- Stack Frame을 저장하는 스택
- 메서드가 수행될 때마다 하나의 스택 프레임이 생성되어 해당 스레드의 JVM stack에 추가
- 메서드가 종료되면 스택 프레임이 제거

#### Native Method Stack

- 자바 외의 언어로 작성된 네이티브 코드를 위한 스택(c/c++ 등)

#### Heap

- 객체를 위한 공간
- Garbage Collection의 대상이 되는 공간
- new 연산자로 생성된 객체 또는 인스턴스와 배열을 저장

#### Method Area

- 클래스의 데이터를 위한 공간
- 자바 프로그램의 실행중 클래스가 사용될 때 해당 영역에서 클래스파일에 대한 정보를 읽어 사용한다
