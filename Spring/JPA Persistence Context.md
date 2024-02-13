JPA Persistence Context, 영속성 컨텍스트

> 프로그래밍에서 영속성이란, 프로그램의 실행과 종료와 연관되어 생명주기를 가지는 객체가 아닌, Database에 저장된 데이터들을 뜻합니다

1. JPA Persistence Context
2. Persistence Context의 장점
3. Entity Manager
4. EntityManagerFactory

## JPA Persistence Context란

JPA를 이해하는데에 있어서 가장 중요한 개념입니다.
애플리케이션과 테이터베이스 사이에 위치해있고, 영구적으로 보관될 객체를 보관하는 가상의 데이터베이스 역할을 하는 존재입니다
EntityManager에 의해 생성되고 관리됩니다

- Transaction 위에서만 제대로 동작합니다

- 스레드 1개당 1개만 생성됩니다

#### Persistence Context의 장점

- 영속성 컨텍스트는 자체적인 캐시를 갖고 있어서 데이터베이스 액세스 횟수를 줄여 성능을 향상시킵니다

- 데이터베이스 테이블과 관련된 복잡한 SQL 쿼리를 작성하는 대신 객체 지향적으로 데이터를 다룰 수 있게합니다

- 데이터베이스 트랜잭션의 일관성과 안전성을 유지하는 데 도움을 줍니다
- 지연로딩 및 지연저장을 제공합니다

> 지연로딩이란, 연관된 객체가 필요한 시점에 데이터베이스에서 로드하게 하는 것  
> 지연저장이란, 변경된 객체를 트랜잭션이 커밋될 때까지 메모리에만 유지하며 실제 데이터베이스에 반영을 미루어 변경사항을 일괄적으로 처리하게 하는 것

## Entity Manager 란

- 영속성 컨텍스트에서 Entity를 관리(저장, 조회, 삭제 등등)합니다
- JPA에서 제공하는 interface로 spring bean으로 등록되어 있어 Autowired로 사용할 수 있습니다
- 생명주기가 있습니다
  > EntityManagerFactory, EntityManagerFactory란 Entity Manager를 생성해주는 역할을 하는 것입니다. DB당 한개씩 생성됩니다

#### Entity의 생명주기

`비영속 상태`  
객체만 생성하고 아직 persist() 메소드를 통해 영속성 컨텍스트에 저장되지 않은 상태

`영속 상태`  
생성된 엔티티가 영속성 컨텍스트에 저장된 상태

`삭제 상태`  
영속성 컨텍스트와 DB 두곳에서 삭제가 된 상태를 삭제 상태
