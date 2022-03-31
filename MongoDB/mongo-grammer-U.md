# mongo-grammer-U

age 가 40 보다 큰 Document 의 status 를 B 로 변환하기

```sql
db.employees.updateMany( { age: { $gt: 40 } }, {$set: { status: "B" } } );
```

users Document 수정 age가 25 보다 작은 Document 의 status를 reject로 수정

```sql
db.users.find({}, { status: 1, _id: 0 })
db.users.updateMany( {age: {$lt: 25}}, {$set: {status:
"reject"} });
```

status 가 pending 인 age 값을 2씩 증가

```sql
db.users.updateMany( { status: "pending"}, { $inc: {age: 2}});
```