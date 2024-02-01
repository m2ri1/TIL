DDL, DML, DCL

## Data Definition Language

데이터 정의어

데이터 정의어란, 데이터베이스를 정의하는 언어를 말하며
데이터를 생성, 수정, 삭제하는 등의 역할을 수행하는 언어입니다

- create : 생성
- alter : 수정
- drop : 삭제
- turncate : 초기화

> 데이터베이스 관리자가 사용합니다

## Data Manipulation Language

데이터 조작어

데이터 조작어란 정의어를 통해서 데이터베이스에 입력된 레코드를 조회, 수정, 삭제하는 역할을 하는 언어를 말합니다

- select : 조회
- insert : 삽입
- update : 수정
- delete : 삭제

응용프로그램, 질의어를 통하여 저장된 데이터들을 기반으로 연산을 수행하는데에 사용됩니다

> 주로 데이터베이스 관리 시스템에서 사용자가 쉽게 사용할 수 있는 인터페이스를 제공합니다

## Data Control Language

데이터베이스에 접근, 권한 부여등의 역할을 하는 언어

- grant : 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 부여
- revoke : 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 **박탈, 회수**
- commit : 트랜잭션의 작업을 저장
- rollback : 트랜잭션의 작업을 취소하거나 원래대로 복구