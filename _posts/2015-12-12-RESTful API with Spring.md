---
layout: post
title: "Start with Spring"
description: "a.k.a한글인코딩과 requestParam삽질"
category: WebServerProgramming
tags: [webframework, spring, utf8, 한글인코딩 ]
imagefeature: 
comments: true
share: true
---

### RESTful API Example

restful api에 처음 도전하는 거라서 예제 코드 조차 감을 잡기 어려웠는데

[spring restful templateExample code](http://howtodoinjava.com/2015/02/20/spring-restful-client-resttemplate-example/)
큰 도움이 되었다. 

* 문제 발생
만들려는 controller의 URI는 아래 모습이었다. 

/api/place/{placeId}/dear/{dear}/post?page={page}

------
1. URI path의 한글 변수 문제
````
@PathVariable("dearName")String dear
````
@PathVariable어노테이션을 사용하고 있었는데 {dear}의 값이 한글로 controller에 넘어오지 못하고 URI요청에서 디코딩 되어 이상한 값으로 넘어왔다. 그래서 이상한 uri로 들어온 요청과 mapping되는 컨트롤러가 없다고 에러가 발생했다.

URI에 있는 값도 utf8로 인코딩해서 받으려면 아래와 같이 하면된다. 
  - tomcat이 설치된 dir를 찾음.(finder사용) 
  - tomcat/conf/server.xml에서 URIEndocing="UTF-8"추가하기.
  - [URI 한글 변수](http://egloos.zum.com/springmvc/v/513986)

p.s: 처음에는 내 웹서버 프로젝트 아래에있는 server.xml을 다 고쳤으나 소용이 없었다.(삽질)
이상한 점이 발견되었다. port가 31337로 설정되어있던데 왜 8080이 아니었을까? 

2. page는 어떤 parameter로 받아야 할까?
URI에서 ?이후로는 파라미터의 URI 주소가 끝나고 parameter가 시작된다.
따라서 page는 parameter이므로  @RequestPram 을 사용해야한다.
또,컨트롤러의 주소 매핑에서도 다시 정확한 주소로 수정해주었다. 

@RequestMapping(value = "/api/place/{placeId}/dear/{dearName}/post


jsp&servlet 처음 배웠을 때 했던 GET,POST 요청에 대한 구분을 다시 확실히 정리해야한다.

[GETvsPost](http://hatssarjy.tistory.com/145)
[쿼리스트링](https://books.google.co.kr/books?id=vlqKBgAAQBAJ&pg=PT261&lpg=PT261&dq=query+string+%EC%9D%B4%EB%9E%80&source=bl&ots=NV2l5WibV5&sig=-XDVQFErhDlkq-i9iHO87uxGRvY&hl=ko&sa=X&ved=0ahUKEwjt-pn7ptbJAhUEtxQKHV9pDk0Q6AEIVTAJ#v=onepage&q=query%20string%20%EC%9D%B4%EB%9E%80&f=false)