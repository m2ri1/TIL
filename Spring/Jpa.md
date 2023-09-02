## Java Persistence API

### ORM 이란?

```
Object-Relational Mapping, 즉 Class와 RDB(Relational DataBase)의 테이블을 매핑하는 것
-> 어플리케이션의 객체를 RDB 테이블에 자동으로 영속화 해주는 것. SQL문이 아닌 Method를 통해 DB를 조작할 수 있게한다
```

---

### JPA 란?

Java에서 ORM(Object-Relational Mapping)을 기술 표준으로 사용하는 인터페이스 모음

**특징과 장점**

- 자바어플리케이션에서 데이터베이스를 사용하는 방식을 정의한 인터페이스
- Hibernate, OpenJPA 등이 JPA를 구현함
- JPA는 매핑된 관계를 이용해서 SQL을 생성하고 실행하는데, 개발자가 SQL을 어떻게 실행시킬지 쉽게 예측 할 수 있게 한다
- 개발자가 SQL아닌 객체 중심으로 개발할 수 있게 한다

**단점**

- 성능 최적화나 복잡한 쿼리를 위해선 JPA만으로는 부족한 경우가 있다
- 잘못 사용하면 성능 문제가 생길 수 있다
