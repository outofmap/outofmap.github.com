---
layout: post
title: "About Event Object, Ajax"                 
description: Javascript      
category: UI
tags: [js,web UI]
comments: true
---

## Event Object
- chrome은 원래 브라우저에서 문서를 제외한 테두리 부분을 chrome을 의미합니다.
- chrome 확장 기능은 그래도 쉽게 만들 수 있어요. chrome에서 제공하는 API를 확인해보세요.
- button : 마우스에서 어떤 키를 눌렀는 지 알려줌 
- KeyboardEvent.MOUSEOVER : element위에 마우스를 올려놓음
- KeyboardEvent.MOUSEOUT : mouse over 되있다가 벗어남 
- relatedTarget : 직전에 있던 곳 

# Ajax (Asynchronous JavaScript and xml)
- XML HttpRequest 객체를 사용하는 비동기 통신 방법
- 서버에서 data를 가져오려면? 
1. url주소를 친다. 2.form을 전송해서 data를 가져온다. 3.현재는 'JSON'을 널리 사용함. 
json: JavaScript Object Notation 
[json] http://www.w3schools.com/js/js_json.asp
- properties : status, readyState, response, responseText, responseXML
- 이벤트 : onreadystatechange 
- 메소드 : 많음 수업자료 참조.
- de facto standard (사실상 표준): 사실상 표준, 사실상의 표준은 관습, 관례, 제품이나 체계가 시장이나 일반 대중에게 독점적 지위를 가진 것을 말한다. 공식적 표준(데 유레 스탠더드)과 반대되는 말로, 영어권에서는 데 팍토 스탠더드(라틴어: de facto /di ˈfæktoʊ/[*] + 영어: standard /ˈstændərd/[*])라고 부름.
[from wiki]

- 자바스크립트의 '동일 출처 정책' : protocol, host name, port Number 중 하나라도 다르면, 데이터를 가져올 수 없다. 
-서버측에서도 HTTP헤더를 통해 외부 출처도 허용해주면 데이터를 가져올 수 있다. Cross Origin Resource Sharing (CORS)

#JSONP 
- script tag 에 json 데이터를 그대로 넣을 수는 없으니까, 
- 예제 코드 : http://dev.epiloum.net/1311

# this
- 모든 함수는 실행할 때 마다 this라는 객체가 추가된다. 
- apply(),call(),bind() 메소드를 사용하면 this를 조작하거나 고정해 둘 수 있다. 


###과제
1. - post data (글 내용, 좋아요 갯수,댓글 갯수,공유 갯수,사람이름, 글 id)
page 1 json
page 2 json ... 5 json까지

2. 좋아요 갯수 변경

3. j,k누르면 포스트 포커스 변경 (수업때 해본 것!)
scrollTo를 사용하세요

----- 

모든 javascript 에서는 prototype 이 숨겨져 있음. [[protoype]] 으로!

[[prototype]]을 연쇄적으로 거슬러 올라가서 프로퍼티를 탐색한다고 하여, prototype chain 이라고 한다.


### Strict mode 
- 문법을 조금 더 엄격하게 검사, 일부 기능이 추가되기도 한다.
- 