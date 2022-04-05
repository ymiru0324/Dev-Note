# mongo-grammer-D

age가 30 보다 작은 Document 삭제하기

```sql
db.employees.deleteMany( {  age: {$lt: 30} } );
```

status가 reject인 document 삭제

```sql
db.users.deleteMany( {status: "reject"} );
```