# MongoDB

NoSQL 사용하는 비관계형 데이터베이스

- DBMS의 한계를 극복
- 스키마 리스
    - 고정된 스키마가 없다
    - RDBMS의 테이블과 달리 데이터를 정해 놓은 필드 형태로 넣어야 한다는 제약이 없다
- 하나의 컬렉션 안에 다양한 데이터 형식을 사용할 수 있다
- 관계형 데이터베이스의 SQL을 사용하지 않는다
    - 데이터 저장, 데이터 조회하는 방법을 별도로 제공
    - 자바스크립트 객체를 그대로 저장할 수 있다
- NoSQL이므로 테이블 개념이 없다
    
    ⇒ 컬렉션에 저장
    

---

## RDBMS와 NoSQL의 차이점

관계형 데이터베이스

- 하나의 고성능 기계에 데이터 저장
- 공통된 형태의 데이터 저장방식 (테이블)
- 공통된 접근방식 (SQL)
- 데이터의 관계를 Foreign Key로 정의하고 이를 이용해 조인 등의 관계형 연산

NoSQL

- 일반적인 서버 수십대를 연결해 데이터를 저장 및 처리하는 구조
- 분산형 구조를 통해 데이터를 여러 대의 서버에 분산해 저장
- 분산 시에 데이터를 상호 복제해 특정 서버에 장애가 발생했을때 데이터 유실인 서비스 중지가 없는 형태
- RDBMS와 다른 형태의 데이터 저장 구조
- RDBMS 복잡도와 용량 한계를 극복하기 위한 목적으로 등장
- 패타바이트 급의 대용량 데이터를 저장 가능
    
    ⇒ 새로운 형태의 데이터 저장기술을 요구
    
- RDBMS와 다른 형태의 데이터 저장 구조
    
    ⇒ RDBMS와 다르게 테이블의 스키마가 유동적
    

| 관계형 데이터베이스 | MongoDB |
| --- | --- |
| Database | Database |
| Table | Collection |
| Table | Collection |
| tuple / row / record | document |
| column | key / field |
| primary key | _id |
| join(table join) | embedded document |

---

## Document

- JSON 기반의 document 기반 데이터 관리
- 데이터 형식
    - 정수(int), 실수(float), 문자열(String)

<aside>
📁 JSON

```json
document = { "id":"01", "language":"java", "edition": { "first": "1st", "second":"2nd", "third":"third" } }
```

</aside>

<aside>
📁 MongoDB

```sql
{
	"_id": ObjectId("5099803df3f42312312391"),
	"username": "gdhong",
	"name": { first: "gildong", last: "Hong" }
}
```

</aside>

## MongoDB 구조

- Database → Collection(Table 대응) → Document(Row 대응)
    - column 개념이 없음(필드 개념 없음)
- NoSQL
    - Collection 에 JSON 형태의 Document 입력
    - Document 한 개가 하나의 로우(레코드)

## MongoDB 특징

- MongoDB Database: database 는 collection 의 집합
- MongoDB Collection: MongoDB Document 의 집합
    - RDBMS Table 과 유사한 개념 단, 정규화된 구조(schema) 정의되어 있지 않다