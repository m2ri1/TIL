## JPA n+1, Fetch join, Entity Graph

Jpa를 사용하다 보면 필수적으로 n+1 문제를 마주하게 됩니다
n+1문제의 원인과 이를 해결하기 위한 방법인 Fetch Join, Entity Graph에 대해 작성하겠습니다

- JPA n+1 문제란
- Fetch Join
- Entity Graph

## JPA n+1 문제란?

연관관계의 매핑된 엔티티를 조회할 경우 조회된 데이터의 개수 n만큼의 쿼리가 더 발생하는 현상을 말합니다
예를들어 class에 소속된 student 객체들을 호출하는 경우, class 의 갯수만큼 불필요한 쿼리가 많이 생기게되어 성능최적화가 되지 않는 것 입니다

#### n+1 문제는 왜 생길까?

findAll()메서드로 조회를 하는 과정에서 jpql이 동작하는데, 이때 중복으로 호출되는 과정이 생기기 때문입니다
이러한 문제는 다음과 같은 방법으로 해결이 가능합니다

## Fetch Join

fetch join 이란 기존에 제공하는 방식과 다르게, 성능 최적화를 위하여 제공하는 SQL의 조인 종류가 아닌 새로운 조인 방식입니다

```java
  @Query("select t from Team t join fetch t.members")
  List<Team> findAllJoinFetch();
```

```java
    // Team 조회
    List<Team> findTeams = TeamRepository.findAllJoinFetch();
	for (Team team : findTeams) {
        System.out.println("team = " + team + ", " + "members = " + team.getMembers());
    }
```

한 엔티티에 연관된 엔티티와 컬렉션을 한 번에 함께 조회할 수 있으므로, 중복 호출이 발생하지 않게됩니다

## Entity Graph

2.1 버전부터 제공하는 엔티티의 연관관계과 있는 객체를 로드할 때 성능을 개선 하기 위한 것입니다
 어노테이션으로 필드명을 지정하면 해당 필드만을 즉시로딩으로 동작하도록 하는 기능을 합니다

```java
 @Query("select t from Team t") @EntityGraph(attributePaths = "members", type = EntityGraph.EntityGraphType.LOAD) List<Team> findAllEntityGraph();
```

#### 지연로딩(Lazy) 이란

필요한 시점에 연관된 객체의 데이터를 불러오는 것(새로운 호출을 생성)

#### 즉시로딩 이란(Eager)

데이터를 조회할 때, 연관된 모든 객체의 데이터까지 한 번에 불러오는 것

#### Fetch Type이란

JPA가 하나의 Entity를 조회할 때, 연관관계에 있는 객체들을 어떻게 가져올 것이냐를 나타내는 설정값

> @xxToOne에서는 EAGER, @xxToMany에서는 LAZY이 디폴드 값 입니다
