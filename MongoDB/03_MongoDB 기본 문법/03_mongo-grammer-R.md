# mongo-grammer-R

```sql
SELECT * FROM people
db.people.find( { } );
```

```sql
SELECT _id, user_id, status FROM people
db.people.find( {}, {_id: 1, user_id: 1, status: 1})
```

```sql
SELECT user_id, status FROM people
db.people.find( {}, {_id: 0, user_id: 1, status: 1})
```

```sql
SELECT * FROM people WHERE status = "A"
db.people.find( { status: "A" } )
```

```sql
SELECT * FROM people WHERE status = "A" AND age = 50
db.people.find( { status: "A", age: 50 } )
```

```sql
SELECT * FROM people WHERE status = "A" OR age = 50
db.people.find( { $or:[ { status: "A" }, { age: 50 } ] )
```

```sql
SELECT * FROM people Where status = "A" AND age = 20;
db.people.find( { status: "A", age: 20 } )
```

```sql
SELECT * FROM people Where status = "A" OR age = 20;
db.people.find( { $or:[ { status: "A" }, { age: 20 } ] );
```

## MongoDB 비교연산자

| 키워드 | 형식 | 설명 |
| --- | --- | --- |
| $lt | < | 작다 |
| $lte | ≤ | 작거나 같다 |
| $gt | > | 크다 |
| $gte | ≥ | 크거나 같다 |
| $ne | ≠ | 같지 않다 |

```sql
SELECT * FROM people WHERE age > 25
db.people.find( { age: { $gt: 25 } } )
```

```sql
SELECT * FROM people WHERE age < 25
db.people.find( { age: { $lt: 25 } } )
```

```sql
SELECT * FROM people WHERE age > 25 AND age <= 50
db.people.find( { age: { $gt: 25, $lte: 50 } } )
```

```sql
SELECT * FROM people WHERE age = 5 or age = 15
db.people.find( { age: { $nin: [ 5, 15 ] } } )
```

```sql
SELECT * FROM people WHERE user_id like “%bc%”
db.people.find( { user_id: /bc/ } )
```

```sql
SELECT * FROM people WHERE user_id like "bc%“
db.people.find( { user_id: /^bc/ } )
```

```sql
SELECT * FROM people WHERE status = "A" ORDER BY user_id ASC
db.people.find( { status: "A" } ).sort( { user_id: 1 } )
```

```sql
SELECT * FROM people WHERE status = "A" ORDER BY user_id DESC
db.people.find( { status: "A" } ).sort( { user_id: -1 } )
```

```sql
SELECT COUNT(*) FROM people
db.people.count()
```

```sql
SELECT COUNT(user_id) FROM people
db.people.count( { user_id: { $exists: true } } )
```

```sql
SELECT COUNT(*) FROM people WHERE age > 30
db.people.count( { age: { $gt: 30 } } )
```

```sql
SELECT DISTINCT(status) FROM people
db.people.distinct( “status” )
```

```sql
SELECT * FROM people LIMIT 1
db.people.find().limit( 1 )
```

---

employees Collection 에서 user_id 가 bcd002 인 Document의 user_id, age, status, _id 출력

```sql
db.employees.find( { user_id: "bcd002" } );
```

employees Collection 에서 user_id 가 bcd003 인 Document의 user_id, age, status 출력

```sql
db.employees.find( { user_id: "bcd003" }, {user_id: 1, age: 1, status: 1, _id: 0 } );
```

employees Collection 에서 user_id 가 bcd004 이거나, age가 28인 Document 의 모든 필드 출력

```sql
db.employees.find( { $or: [ { user_id: "bcd004" }, { age: 28 } ] );
```

age 가 30 보다 큰 Document 의 user_id, age, _id 출력하기

```sql
db.employees.find( { age: { $gt:30 } }, { user_id: 1, age:1, _id: 1 } );
```

age 가 50 이고 status 가 A 인 Document 의 user_id 만 출력하기

```sql
db.employees.find( { age: 50, status: "A" }, { user_id: 1, _id : 0 } );
```

age 가 30 보다 작은 Document 의 user_id 와 age 출력하기

```sql
db.employees.find( { age: { $lt:30 } }, { user_id: 1, age:1 } );
```

user_id 종류 출력하기

```sql
db.employees.distinct( "user_id" );
```

user_id 가 bcd 로 시작하는 전체 Document 출력하기

```sql
db.employees.find( { user_id: /^bcd/ } );
```

user_id 에서 cd 문자를 포함하는 전체 Document 출력하기

```sql
db.employees.find( { user_id: /cd/ });
```

users Document 검색 age가 18 보다 큰 Document의 name 출력하기

```sql
db.users.find( { age: { $gt: 18 }}, { name: 1, _id: 0} );
```