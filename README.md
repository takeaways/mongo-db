# mongo-db

몽고디비 학습하기

#### 몽고디비 유래

1. Humongouse : 휴몽고스, 거대한

#### 다운로드

1. https://mongodb.com 에서 운영환경에 맞게 다운로드 하면됩니다.
2. Program Files/MongoDB/Server/3.2/bin 환경변수를 설정한다.

#### data, log 폴더 생성

1. 데이터 폴더 : C:\Program Files\MongoDB\data
2. 로그 폴더 : C:\Program Files\MongoDB\log

#### MongoDB 실행

- 서버를 실행시킬때 데이터 폴더 경로를 꼭 지정해줘야 한다

1. mongod.exe --dbpath "C:\Program Files\MongoDB\data"

or

2. mongod --dbpath "C:\Program Files\MongoDB\data"

#### 몽고디비 자동 실행을 위한 설정

1. mongod.cfg 파일 만들기
   <pre>
   <code>
   #데이터베이스 폴더
   dbpatch = C:\Program Files\MongoDB\data

# mongod 포트

port = 27017

# 로그파일

logpath = C:\Program Files\MongoDB\logs\mongo.log

#웹 관리 사용
rest = true
</code>

</pre>
2. 윈도우 서비스 등록하기
- "C:\Program Files\MongoDB\Server\4.2\bin\mongod.exe" -f "C:\Program Files\MongoDB\mongod.cfg" -install

#### 접속 및 확인

1. mongo
2. show dbs
3. use dbname
4. show tables (테이블 컬렉션)
5. db.TABLE.find().pretty()

# 02) MongoDB 개념과 RDBMS 비교

1. 대용량 빅 데이터에 적합한 NoSQL 데이터 베이스입니다.
2. NoSQL 데이터 베이스 중 사용 인지도 1위이다.
3. 구글, 페이스북, 포스퀘어, 이베이 등 주요 대기업 에서 사용

## NoSQL이란?

1. SQL = Structured Query Language (구조적 질의 언어)
2. NoSQL = No Structore Query Language (구조가 없는 질의 언어)

- 즉 table(Collection) 에서 스키마를 가지고 있지 않음
- 지정된 데이터 형식이 없고 넣고 싶은 데이터 형식을 마음대로 넣을 수 있다.

## Collection 과 Documente 란?

1. RDBMS = 테이블, 데이터(Row)
2. MongoDB = Collection, Document

## RDBMS Table의 구조

1. RDBMS의 테이블은 스키마를 가지고 있고 고정된 구조 이다. (SQL)

- select \* from g5;
- select CU.userName, G.channelId from Channel_User as CU
  join Group as G on CU.groupId = G.id
  where CU.userId = 3
- N : M 의 경우에는 테이블이 하나더 생성된다.

## MongoDB의 구조

1. 테이블을 생성하지 않아도 insert하면 테이블이 바로 생성된다.
2. 여러개의 테이블 구조를 배열 형태로 하나의 컬렉션으로 관리할 수 다. (데이터를 읽을 때 join 하는 구조가 아니라 데이터를 생성할 때 join을 하게 된다.)
3. 고정된 스키마로부터 구애 받지 않고 자유로운 문서 지향 데잍베이스 이다.
4. 다양한 타입지원 : String, Integer, Boolean, Arrays, Timestamp, Data, Object등 여러 데이터 타입을 지원한다.
5. 읽기 쓰기 효율을 높이고 자동으로 장애 조치를 하고 확장이 용이함 (특별한 경우를 제외하고 오류가 잘안남)
6. 여러 서버에 분산 저장 및 확장이 용이하며(Sharding - 파편화), 방대한 데이터 처리가 (빅데이터) 빠르다는 장점이 있다.

- mongo
- show dbs : 디비 목록보기
- use dbname : 디비로 접속 하기
- show tables : 테이블 목록 보기
- db.g5_geonil.find().pretty() : 테이블 내용 보기
  <pre>
  <h1>insert 하는 방법</h1>
  <ul>
  <li>입력 하는 데이터 틀에 제약없이 막 넣을 수 있다.</li>
  </ul>
  <code>
  #현재의 데이터 베이스 db 로 접근이 가능하다.
  db.g5_geonil.insert({
    "user_id":1,
    "user_name":"geonil",
    "subjects":[
      {
        "title":"수학",
        "score":10
      },{
        "title":"국어",
        "score":9
      },{
        "title":"영어",
        "score":10
      },
    ],
    "hit":1000
  });
  </code>
  </pre>
