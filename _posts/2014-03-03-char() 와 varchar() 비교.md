---
layout: post
title: "char() vs varchar()"
description: "web server Project"
category: webServer
tags: [webserver, mysql]
imagefeature: 
comments: true
share: true
---
char() 와 varchar() 비교

char() : 고정문자 길이. 고정문자는 ex.도시명 처럼 길이의 제약이 있는 경우 사용하면
나중에 검색할 때 성능, 메모리 면에서 유리

varchar() : 가변문자길이. ex.주소 처럼 얼마나 길지 알 수 없을 때 사용하면 좋음.

TINYIN() : 음수를 사용할 일이 없는 경우 UNSIGNED 를 해야 더 많은 숫자를 표현할 수 있음.

FLOAT / DOUBLE(.) : 소수 표현


INSERT 삽입

2가지 방식이 있어요!

1. INSERT INTO table_name VALUES (value1, value2, value3,...)
컴럼의 순서대로 value 를 넣어줌.
- 장점: 귀찮게 컬럼을 안써도된디.
- 단점: 컬럼의 순서대로 써야하고, value를 빼먹고 쓸 수는 없다.
2. INSERT INTO table_name (column1, column2, column3,...) VALUES (value1, value2, value3,...)
컬럼을 먼저 쓰고 value를 써줌.
- 장점: 컬럼이 만들어진 순서대로 쓰지 않아도 되고, value를 빼고 쓸 수도 있다.
- table의 구조가 바뀔 때도 있는 데, 그래서 컬럼을 함꼐 써주는게 더 좋을 수도
- 단점: 귀찮음ㅋㅋㅋ

DELETE

DELETE FROM 테이블명 [WHERE 삭제하려는 칼럼 명=값];
DELETE FROM student WHERE id = 2;

- TRUNCATE : 테이블의 전체 데이터를 삭제

TRUNCATE 테이블명;
TRUNCATE student;

-DROP : 테이블을 삭제
DROP TABLE 테이블명;

SELECT

SELECT 칼럼명1, 칼럼명2 
    [FROM 테이블명 ] 
    [GROUP BY 칼럼명] 
    [ORDER BY 칼럼명 [ASC | DESC]] 
    [LIMIT offset, 조회 할 행의 수]

    [] 는 옵션으로 생략할 수 있지만, 순서는 이대로 지켜야함 

SELECT * FROM 테이블명 GROUP BY 그룹핑 할 기준 칼럼명
SELECT * FROM 테이블명 ORDER BY 정렬의 기준으로 사용할 열 [DESC | ASC]
DESCENDENT 

ex. 
select * from student order by distance desc;
select * from student order by distance desc, address asc;
distance를 기준으로 먼저 desc로 정렬하고, 동일한 경우 address를 기준으로 asc 정렬함.

Database Access Object 
