---
layout: post
title: "Spring mvc setting"
description: "web resources 설정"
category: webServer
tags: [webframework, spring, setting ]
imagefeature: 
comments: true
share: true
---

####spring project에서 web resources 찾을 수 있도록 설정하기

* 프로젝트의 project-servlet.xml 파일에 아래 코드 추가 

```
<mvc:resources location="/stylesheets/" mapping="/stylesheets/**" />
	<mvc:resources location="/javascripts/" mapping="/javascripts/**" />
	<mvc:resources location="/images/" mapping="/images/**" />
```

location="/디렉토리명/" mapping="/디렉토리명/**" 입니다.   

이렇게 하면 spring에서도  css,javascript,image file 적용가능.

### web resource 이름으로 url에서 접근을 막는 법

* 보안상의 이유 또는 다른 이유로 jsp 이름으로 접근하지 못하게 하려면, 

1. WEB-INF 아래에 새로운 folder생성 (ex.이름이 jsp인 폴더)
2. jsp 안에 jsp파일들을 다 넣어준다. (commons 디렉토리에도 jsp파일이 있다면 commons도 WEB-INF 하위로 이동)

이렇게하면, Servlet의 정책에 따라 WEB-INF 안의 자원에 사용자가 직접 접근하지 못하게 하고 있어서 404에러가 뜨면서 접근할 수 없게 됩니다.

----------------------

dispatcherServlet이 있어서 webservlet 어노테이션이 없어도 동작가능한 것임!
dispatcherServlet는 frontController로 모든 url에 대한 mapping을 할 수 있음. 
