---
layout: post
title: "[Database] SQL 이란?" 
tags: [DB,DATABASE,SQL,DDL,DML,DCL]
categories: [Database]
banner:
  image: "/assets/images/banners/22/04/SQL.png "
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

## SQL 이란 ? 
***
<img src="/assets/images/img/Gitblog_img/22/04/27/SQL_01.PNG"> 
SQL(Structured Query Language, 구조적 질의 언어)은 관계형 데이터베이스 시스템(RDBMS)을 제어하는 컴퓨터 언어이다.
SQL은 1970년대에 IBM에서 최초로 개발되었으며 관계형 모델이라는 이론에서 파생된 특징을 가지고 있는데,   
현재 SQL의 표준으로 ANSI SQL이 정립되었다. 
각 DBMS 프로그램에서 ANSI SQL을 기반으로 
개발된 개별 SQL 을 사용하며 서로 근소한 차이를 보인다.

간략요약 : SQL은 데이터를 저장하고 관리하는 커다란 체계

##  SQL 쿼리문 의 분류 
***
SQL 쿼리문의 역할에 따라 3가지로 분류된다.

- DDL(Data Definition Language, 데이터 정의어)  
각 릴레이션을 정의하기 위해 사용하는 언어이다. (CREATE, ALTER, DROP...)

- DML(Data Manipulation Language, 데이터 조작 언어)
데이터를 추가/수정/삭제하기 위한, 즉 데이터관리 를 위한 언어이다. (SELECT, INSERT, UPDATE...)

- DCL(Data Control Language, 데이터 제어 언어)
사용자 관리 및 사용자별로 릴레이션 또는 데이터를 관리하고 접근하는 권한을 다루기 위한 언어이다. (GRANT, DENY, REVOKE...)

 ⭐️ 개발자가 일반적으로 DB를 사용할 때 사용하는 언어의 중요도는 <U> DML > DDL > DCL </U> 순이다.
DB를 조회하고, 조회하는 DML을 가장 많이 사용하고, DB의 테이블 스키마(설계 수준)를 수정하는 DDL을  그 다음 많이 쓴다.

DCL은 DBA(dataBaseAdminstation, 데이터베이스 관리자) 가 주로 사용하며 일반 개발자는 사용하는 일이 드물다.


## SQL의 언어 특성
***
각 프로그래밍 언어가 가진 고유한 특성은 꼭 구별 지어 알아두어야 사용할 때 오류를 줄잀 수 있다.
SQL은 다음과 같은 언어적 특성을 갖는다.


1. SQL은 대소문자를 가리지 않는다.
(단 , 서버 환경이나 DBMS 종류에 따라 데이터베이스 또는 필드명에 대해 대소문자를 구분한다.)
2. SQL명령은 반ㄷ시 세미클론(;)으로 끝나야 한다.
3. 고유의 값은 따옴표("")로 감싸준다.

~~~
SELECT * FROM EMP WHERE NAME = 'James'`;  
~~~

4. SQL에서 객체를 나타낼 때는 백틱('')으로 감사쭘

~~~
SLECT 'COST', `TYPE` FROM `INVOICE`;
~~~

5. 주석은 일종의 도움말로 주석 처리된 문장은 프로그램에서 동작하지 않는다.
한 줄 주석은 문장 앞에 `--` 를 붙여서 사용한다.

~~~    
ex) SELECT * FROM EMP; dl 쿼리는 실행되지 않는다.
~~~


6. 여러 줄 주석 /* */ 로 깜싸준다.

~~~
ex) `SELECT * FROM EMP WHERE NAME = 'James'`;
~~~

## SQL 명령어 


### DDL (데이터 정의 언어)
***
데이터베이스 스키마와 설명을 처리하도록 정의하는 언어로 , 데이터베이스나 테이블 생성/변경/삭제 등의 작업이 포함

CREATE (데이터베이스 개체(테이블, 인덱스, 제약조건 등) 정의 
~~~
--데이터베이스 생성
CREATE DATABASE [NAME];

--테이블 생성
CREATE TABLE [NAME];
~~~

DROP(데이터베이스 개체 삭제) 삭제
~~~
--데이터베이스 삭제
DROP DATABASE [NAME];
--테이블 삭제
DROP TABLE [NAME];
~~~

ALTER(데이터베이스 개체 정의 변경) 테이블 내용 수정
~~~
--컬럼 추가
ALTER TABLE [TABLE_NAME]
ADD [COLUMN_NAME] datatype;

--컬럼 삭제
ALTER TABLE [TABLE_NAME]
DROP COLUMN [COLUMN_NAME];

--컬럼 수정
ALTER TABLE [TABLE_NAME]
MODIFY COLUMN [COLUMN_NAME] datatype;

-- Fk 설정
ALTER TABLE [TABLE_NAME]
ADD FOREIGN KEY (column_name) REFERENCES [TABLE_NAME] (column_name);
~~~

TRUNCATE : 데이터 삭제
~~~
TRUNCATE TABLE [TABLE_NAME];
~~~

RENAME : 이름 변경
~~~
RENAME TABLE [TABLE_NAME] TO [NEW_TABLE_NAME];
~~~

~~~
DROP, TRUNCATE,DELETE의 차이 
- DELETE 명령어는 데이터는 지워져도 테이블의 용량은 줄어 들지 않고 ROLLBACK을 통해
데이터를 복구할 수 있다.

- TRUNCATE 명령어는 용량이 줄어 들고, 인덱스 등 모두 삭제가 되지만 데이터를 복구할 수 없다.

- DROP 명령어는 테이블 자체를 삭제한다. 삭제 후 되돌릴 수 없다.
~~~


### DML (데이터 조작 언어)
***
데이터 검색 , 삽입 , 변경, 삭제 수행 조작하는 언어로 실질적으로 저장된 데이터를 관리하고 처리할때 사용


#### SELECT(테이블 데이터의 검색 결과 집합의 취득) : 조회 
~~~
SELECT * 
FROM [TABLE_NAME];
~~~

#### INSERT(행 데이터 또는 테이블 데이터의 삽입)
~~~
INSERT INTO [TABLE_NAME] (column, column, ...) 
VALUES (value, value, ...);
~~~

#### UPDATE : 수정
~~~
UPDATE [TABLE_NAME] 
SET column = value, ... 
WHERE condition;
~~~

#### DELETE : 데이터 삭제
~~~
DELETE FROM [TABLE_NAME] WHERE condition;
~~~


### DCL(Data Control Language)
***
데이터의 보안성, 무결성, 회복, 병행, 수행제어 등을 정의하는 데 사용한다. 명령어로는 ROLLBACK,  
COMMIT, GRANT, REVOKE등이 있다.

#### COMMIT 
작업했던 내용을 완전히 저장(COMMIT 후에는 ROLLBACK을 할 수 없다)
~~~
-- INSERT, UPDATE, DELETE 등의 작업을 수행한 후 완전히 저장

COMMIT;
~~~

#### ROLLBACK
작업했던 내용을 원래대로 복구
~~~
-- INSERT, UPDATE, DELETE 등의 작업을 수행한 후 원래 상태로 되돌린다
-- DROP, TRUCATE등은 ROLLBACK이 불가하다.

ROLLBACK;
~~~

#### GRANT 
사용자에게 권한 부여 
~~~
-- 사용자 권한 부여
GRANT ALL PRIVILEGES ON [DB_NAME.TABLE_NAME]TO [user_name@host] IDENTIFIEDBY [PASSWORLD]

--- 설정한 권한 적용 명령어
FLASH PRIVILEGES;
~~~

#### REVOKE
GRANT로 부여한 권한을 해제
~~~
--전체 권한 해제 명령어
REVOKE ALL ON [DB_NAME.TABLE_NAME] TO [user_name@host];
--특정 권한 해제 명령어
REVOKE INSERT, UPDATE, CREATE, ... ON [DB_NAME.TABLE_NAME] TO [user_name@host];

--권한 확인 명령어
SHOW GRANTS FOR [user_name@host];
~~~


## PK (Primary Key) / FK (Foreign key)
***

테이블의 필수 요소로써 모든 테이블은 이들 둘 중 하나 이상을 반드시 포함하고 있다.


#### Primary Key 설정
~~~
CREATE TABLE 테이블 ( 
...
CONSTRAINT 제약_조건_이름 PRIBARY KEY (컬럼)
)
~~~

~~~
CREATE TABLE 테이블 (
컬럼 데이터타입 CONSTRAINT 제약_조건_이름 PRIMARY KEY,
...
)
~~~

- 테이블을 생성할 때 PK를 정의한다.
- PK는 각 행을 고유하게 식별하는 역할을 담당한다.
- 테이블당 하나만 정의 가능하다.
- 지정된 컬럼에는 중복된 값이다 NULL값이 입력될 수 없다..
     ㄴ NOT NULL + UNIQUE(UK)를 한 것과 같은 기능을 한다.
- PK로 지정 가능한 컬럼이 여러 개 있을 때는 검색에 많이 사용되고 간단하고 짧은 컬럼을 지정한다.
- 주 식별자 , 주키 등으로 불린다.
- 고유 인덱스(Unique index)가 자동으로 생성된다.

❖ 예제 
~~~
create table dept(

dno varchar2(14),

dname varchar2(14),

loc varchar2(8),

director varchar2(4),

constraint dept_dno_pk primary key (dno)

);

~~~
table DEPT가 생성되었다.

#### Foreign Key(FK)

<img src="/assets/images/img/Gitblog_img/22/04/27/student.png"> 
FK는 참조하는 테이블과 참조되는 테이블의 관계를 나타낸다. 
그림에서 학생 - 수업 테이블은 학생테이블과 수업테이블의 관계를 1:N 관계로 나타내기 위한 테이블이므로 
학생테이블과 수업 테이블을 참조해 만들어야 한다.
그러기 위해선 학생정보를 식별하는 학생코드(PK) , 수업정보를 식별하는 수업코드(PK)로 테이블이 구성되며
이렇게 다른 테이블의 정보를 참조하기 위한 학생코드와 수업코드는 학생_수업테이블 내에 FK(외래키)가 된다.

학생과 수업 테이블의 PK가 학생-수업 테이블에서 FK가 되며 
이는 학생-수업테이블은 학생과 수업테이블을 참조하는 테이블이라는 의미를 표현하며
동시에 학생과 수업테이블은 학생-수업테이블에 의해 참조되는 테이블로 서로의 관계를 알 수 있게 된다.


#### Foreign Key 설정 
~~~
CREATE TABLE 테이블(

…

CONSTRAINT 제약_조건_이름 FOREIGN KEY (컬럼)

REFERENCES 참조할_테이블 (참조할_컬럼)

[ON DELETE CASCADE | ON DELETE SET NULL]

);
~~~