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
