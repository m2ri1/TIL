## Database

#### 데이터베이스란?

전자적으로, 체계적으로 저장되어있는 데이터들의 모음을 가르키는 말입니다

- 데이터베이스의 특징
- 식별자 란?
- RDBMS 란?
- 비관계형 데이터베이스 란?
- DBMS 란?
- SQL 이란?

위 주제들에 대해서 작성해보겠습니다

## 데이터베이스의 특징

- 데이터베이스 관리시스템을 사용하여 데이터를 저장, 검색 및 편집을 할 수 있습니다
- 서버에서 필요한 대량의 데이터를 저장하고, 관리하는데에 꼭 필요합니다

데이터베이스는 기준에 따라 세가지 유형으로 구분할 수 있습니다

- 문서 텍스트, 통계 또는 멀티미디어 객체와 같은 콘텐츠
- 회계, 영화 또는 제조와 같은 적용 분야
- 데이터베이스 구조 또는 인터페이스 유형과 같은 기술적 측면

#### 식별자 란?

데이터베이스에서 식별자란
하나의 엔티티에 구성되어있는 여러개의 속성과 값들중 유일한 값으로, 엔티티를 대표하여 다른 엔티티들과 식별할 수 있도록 하는 값을 말합니다

`유일성`, `최소성`, `불변성`, `존재성`을 가지며
이를 통해 아래와 같은 특징을 가집니다

- 식별자는 하나의 엔터티안에 최소한으로 가지고있어야 합니다
- 한번 지정된 식별자의 값은 변할 수 없습니다
- null값을 허용하지 않습니다

---

### 관계형 데이터베이스 (RDBMS)

관계형 데이터베이스란?  
서로 다른 데이터 구조가 서로 관계를 가지고 데이터를 구성할 수 있게하는 정보 모음을 말합니다

- 테이블, 행, 열의 정보를 구조화하는 방식을 사용합니다

  > 따라서 여러 데이터 포인트 간의 관계를 쉽게 이해하고 정보를 얻을 수 있습니다

- 대량의 구조화된 데이터를 관리해야 하는 조직에서 가장 많이 사용됩니다

#### 장점

- 전체 데이터베이스 구조를 변경하거나 기존 애플리케이션에 영향을 주지 않고 필요할 때마다 간편하게 데이터를 변경할 수 있습니다

- 정규화 데이터베이스 기법을 사용하여 데이터 중복성을 줄이고 데이터 무결성을 개선할 수 있습니다

#### 단점

- 기존에 작성된 스키마를 수정하기 어렵습니다

- 데이터베이스의 부하를 분석하기 어렵습니다

- 빅데이터를 처리하는데 매우 비효율적입니다

---

### 비관계형 데이터베이스

기존의 관계형 데이터베이스의 한계를 뛰어넘기 위해 만들어진 새로운 형태의 데이터베이스입니다

- 거대한 Map으로서 key-value 형식을 지원합니다

- 관계형 db와 달리 PK,FK JOIN등 관계를 정의하지 않습니다

- 스키마에 대한 정의가 없습니다

#### 장점

- 대용량 데이터 처리를 하는데 효율적입니다
- 관계형 데이터베이스에 비해 쓰기와 읽기 성능이 빠릅니다
- 복잡한 데이터 구조를 표현할 수 있습니다

#### 단점

- 큰 크기의 document를 다룰 때는 성능이 저하됩니다  
  (쿼리 처리시 데이터를 파싱 후 연산을 해야하기 때문)

---

### 데이터베이스 관리시스템 (DBMS)

DBMS란?

데이터를 한곳에 모은 저장소를 만들고 여러 사용자가 접근하여 데이터를 저장 및 관리 등의 기능을 수행하며 공유할 수 있게 하는 응용 소프트웨어 프로그램입니다

DBMS는 각기 비슷한 역할을 수행하지만, 다음과 같이 여러종류가 있습니다

#### 관계형 데이터베이스 관리 시스템(RDBMS)

- NoSQL DBMS
- 인 메모리 데이터베이스 관리 시스템(IMDBMS)
- 기둥형 데이터베이스 관리 시스템(CDBMS)

또는 다음과 같이 분류합니다

- 계층형(Hierarchical)
- 망형(Network)
- 관계형(Relational)
- 객체지향형(Object-Oriented)
- 객체관계형(Object-Relational)

대표적인 DBMS 프로그램들은 다음과 같습니다

- Oracle
- MySQL
- MSSQL
- MariaDB

---

### SQL

SQL(Structured Query Language) 이란?

국제표준화기구에서 표준을 정해서 발표하고 있는,
관계형 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어를 말합니다

- 표준 SQL을 익히면 대부분의 DBMS에 공통적으로 적용할 수 있습니다