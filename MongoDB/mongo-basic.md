# mongo-basic

## MongoDB Shell실습

1. MongoDB 데몬 실행
D:
cd D:\Dev\MongoDB\bin\
mongod --dbpath D:\Dev\data\db
2. MongoDB실행
D:
cd D:\Dev\MongoDB\bin\
mongo

## 간단한 명령어

show dbs // 데이터베이스 확인
use mongodb_basic // mongodb_basic 데이터베이스 생성
db.sample.insert({"name":"홍길동"}); // collection 생성, document name에 홍길동 생성
db.sample.find() // 데이터베이스 조회
db.sample.save({name: "test", age:26}); // document 생성
db.sample.find().pretty() // ^예^쁘^게^ 보여줌
db.sample.remove({}); // sample 제거

### mongodb_basic 제거

use mongodb_basic  // mongodb_basic  접속
db.dropDatabase() // 제거
show dbs // 제거된지 확인

db.shutdownServer(); // 데몬 종료