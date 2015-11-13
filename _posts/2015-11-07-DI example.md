---
layout: post
title: "Spring DI example"
description: "DI example in project"
category: webServer
tags: [webframework, spring, Dependency Injection ]
imagefeature: 
comments: true
share: true
---

### spring을 사용해 DI 구현하기
* 프로젝트의 resources 패키지를 생성 > 이 패키지 안에 spring bean configuration 생성 > file name : di.xml 로 생성 > namespace 중  p 선택 > 완료.

* di.xml에 bean추가하기

<beans/> 하위에 <bean id="interface name" class="구현클래스이름+자동완성"/> 으로 원래 소스코드에서 new로 직접 생성했던 것을 대신 해줄 수 있다. 

```
<bean id="messageProvider" class="net.slipp.di.HelloWorldMessageProvider" />
	<bean id="messageRenderer" class="net.slipp.di.MessageRender">
		<property name="messageProvider" ref="messageProvider" />
	</bean>	
```

* property name 과 ref 설정의 의미? messageRender class의 속성으로 messgaeProvider가 있고 참조 class명을 적어주는건가요?


### xml의 주석처리 방식

* 주석은 <!--로 시작하여 -->로 끝납니다. 예를 들어, <!--catalog last updated 2000-11-01-->과 같습니다.
<!-- 주석은 이렇게 ㅠㅠ -->

### spring test 하기

```
	ApplicationContext ac = new ClassPathXmlApplicationContext("di.xml");
			MessageRender renderer = (MessageRender)ac.getBean("messageRenderer");
```

이 코드는 여전히 생소하기도 하고, 테스트도 어렵다. 그래서 쉽게 테스트 할 수 있는 방법을 알아보자!

1. junitTest class만들기
2. poxm.xml에  spring-test lib가 없다면,

```      
<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-test</artifactId>
			<version>4.2.2.RELEASE</version>
		</dependency>
```

version을 적절히 선택해서 위 코드 추가. 
3. 다시 Test클래스에서     
@RunWith(SpringJUnit4ClassRunner.class) 추가.

4. @ContextConfiguration("classpath:/di.xml") 도 추가.

5. test하고 싶은 class의 인스턴트가 필요하죠? 

@Autowired라는 annotation을 활용하면 di.xml에서 해당하는 인스턴트를 찾아서 연결해줘요.

```
@Autowired
	private MessageRender messageRenderer;
```

6. test메소드에서 test를 실행합니다.

```
@Test
	public void renderer() {
		messageRenderer.render();
	}
```

### 환경설정에 필요한 annotation 설정 저장하기

1. 환경설정 > template > new 

2. 이름을 정하고 (ex.springtest) 
필요한 annotion set를 아래와 같이 복붙 후 ok. 

${is1:import('org.junit.runner.RunWith')}${is2:import('org.springframework.test.context.ContextConfiguration')}${is3:import('org.springframework.test.context.junit4.SpringJUnit4ClassRunner')}@RunWith(SpringJUnit4ClassRunner.class)@ContextConfiguration("classpath:/di.xml")

3. 이후에는 springtest 만 입력 후 자동완성하면 어노테이션이 자동 추가 된다!




