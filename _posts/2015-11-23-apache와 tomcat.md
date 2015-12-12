---
layout: post
title: "apache와 tomcat"
description: "서버의 구성"
category: Webserver
tags: [배포, apache, tomcat]
imagefeature: 
comments: true
share: true
---
#### apache 와 tomcat

Q. apache는 배포서버에서 꼭 다운 받아야하나요?
중간에 apche나 nginX가 있다면, 웹 브라우저 -> apache / nginX -> tomcat 으로 거쳐가게 할 수 있다.

< apache vs tomcat >
공통점 : apache, tomcat모두 웹서버이다. 
차이점 : 
* tomcat은 동적인 web app을 만드는데 특화되어있다. 반면에, apache 정적인 web app만 만들 수있다.
* apache기 있고, 사용자가 정적인 자원을 요청하는 경우, apache에서 tomcat까지 가지않고 바로 자신이 알고있는 directory path에서 바로 찾아서 보내준다.

  
Q.apache를 거쳐가게 하면 느리지 않을까? 느려질 수도 있는데 왜 쓰지?
* tomcat은 정적인 자원은 apache에 비해 매우 느리게 준다. 비용이 많이든다. 그래서 apache와 tomcat의 각각의 장점을 모두 취하는 방식이다 apache 와 tomcat을 모두 사용하는 것이다.
* tomcat server 점검하려면, tomcat을 꺼야하는데 사용자에게 아무것도 못보여준다.
그래서 apache가 tomcat을 바라보게 하고있다가 점검페이지를 바라보게 바꿀 수 있음.
* apache와 tomcat을 같은공간에 설치하면, 네트워크 비용이 거의 들지 않는다. 
  * cache server -> Apache -> tomcat으로 서버를 구성할 수도 있다. 
  cache server : 사람들이 자주 찾는 자원(data)가 있을 때, 이 데이터를 메모리에 저장해둔다. 그러면 인기있는 요청에 빠르게 대응할 수 있고, 매번 자원 위치까지 찾아가는 비용을 줄일 수 있다.


### H2 메모리 DB

내장 데이터 베이스? 
* 내장 데이터베이스가 가볍다는(lightweight) 특성때문에 프로젝트의 개발단계에서 내장 데이터베이스는 유용한다. 설정이 쉽고 빠르게 시작할 수 있고 테스트가능하며 개발중에 SQL을 빠르게 발전시킬 수 있다는 장점이 있다.

|remote서버|
|----
|RAM(JVM)|
|HDD|

HDD: mysql(DB Server) / file server / program byte code

H2는 내장 데이터 베이스라서 RAM에서 생성되고, 서버가 종료되면 함께 사라짐.
다른 DB처럼 추가 설치 과정이 필요없음.

Q.개발서버의 HDD용량은 많이 필요하지 않고, 프로그램 코드를 저장할 정도만 되면 괜찮지 않을까? 
  - 실제로 요즘은 서버의 BDD용량은 적게, RAM 용량은 크게 선택하는 경우가 많다. 
만약 file server와 DB서버가 따로 있다면, 파일서버는 HDD용량을 크게, RAM용량은 조금 부족해도 괜찮다. 반대로,DB서버는 연산이 많이 일어나니까 HDD용량도 커야하지만,RAM용량도 커야함. 