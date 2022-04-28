---
layout: post
title: "[Database] 쿼리(query)란 무엇인가?  " 
tags: [Programming,data,database,query]
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

## 쿼리(Query)란 무엇인가?
쿼리(Query)는 질문, 문의하다라는 뜻이다. 질문하면 답을 달라는 일종의 요청(데이터베이스에 정보를 요청하는 것)이다.  
ex ) 구글, 다음 등 검색창에 'Database' 라는 검색어를 쳐보면 , Database에 대한 정보들이 쏟아져 나올 것이다.  
이 정보들은 모두 서버에 저장되어 있던 데이터베이스에서 온 것들이다. 내가 'Database'에 대한 데이터를 달라는 쿼리를   
주었고, 서버가 이에 응답해 데이터베이스에서 데이터를 보여준 것이다.

흔히 ' 쿼리문을 작성한다' 는 말을 많이 사용하는데, 이 말은 <U>데이터베이스에서 원하는 정보를 가져오는 코드를 작성한다.</U>
정도로 이해하면 된다. 쿼리문을 잘 작성한다는 것은 데이터베이스에서 필요한 데이터에 빠르게 접근하고, 데이터를 능숙하게 핸들링한다는 말로도 볼 수 있다.

과정예시  
사용자 -> 질의(쿼리문) -> DB서버 -> 결과 -> 사용자


### 기본 SQL 쿼리문 (형식)
~~~

01. SELECT : select 열 이름 from 테이블명 where 조건 ; 

02. INSERT : insert into 테이블명 ( 추가하고자 하는 열이름) values();

03. DELETE : delete from 테이블명 where 조건;

04. UPDATE : update 테이블명 set 수정하고자 하는 컬럼명 = 수정하는 값 
~~~