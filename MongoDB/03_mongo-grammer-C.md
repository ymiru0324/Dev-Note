# mongo-grammer-C

employees Collection 생성

```sql
db.createCollection("employees");
```

다음 Document 데이터 넣기

- user_id 가 bcd001, age 가 45, status 가 A 인 Document
- user_id 가 bcd002, age 가 25, status 가 B 인 Document
- user_id 가 bcd003, age 가 50, status 가 A 인 Document
- user_id 가 bcd004, age 가 35, status 가 A 인 Document
- user_id 가 abc001, age 가 28, status 가 B 인 Document

```sql
db.employees.insertMany(
	[ 
		{ user_id: "bcd001", age: 45, status: "A" },
		{ user_id: "bcd002", age: 25, status: "B" },
		{ user_id: "bcd003", age: 50, status: "A" },
		{ user_id: "bcd004", age: 35, status: "A" },
		{ user_id: "abc001", age: 28, status: "B" }
	]
);
```

name이 sue, age가 26, status가 pending인 Document

```sql
db.users.insertOne( { name: "sue", age: 26, status: "pending" });
```