---
layout: post
title: "Jsp와 servlet"
description: "web server Project"
category: webServer
tags: [webserver, log]
imagefeature: 
comments: true
share: true
---
###문제점
- 코드가 많이 지니까 java코드가 섞이면서 jsp가 복잡하고 알아보기 어려워졌음. 
- jsp가 너무 많은 일을 할 수록 유지 보수가 어려워짐.

###해결책
- 역할을 분리하자!
- MVC (Model, View, Controler) 
**Model**
핵심적인 비즈니스 로직을 담당,DB와 인터페이스 (.java)
**View**
화면에 보여지는 것을 담당 (jsp)
**Controler.
로직을 처리하고 결과에 대해서 예외처리하는 일 담당 (servlet)

***
properties - build path - output folder 설정