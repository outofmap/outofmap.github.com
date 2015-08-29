---
layout: post
title: "logging Framework"
description: "web server Project"
category: webServer
tags: [webserver, log]
imagefeature: 
comments: true
share: true
---
# 로그에도 레벨이 있음!
debug < info < warn < error 

- debug 메시지가 많아지면 성능에 문제가 생길 수 있음.
- logback.xml에서 남기고 싶은 로그의 level을 지정할 수 있음.
ex. level="warn"인 경우 debug메시지는 warn 이상부터 남음.
-개발단계에서는 debug로 설정, 서비스 시작 이후에는 info or warning으로 설정.
