javabean

name을 호출하고 싶을 때 name이 private이라면

ex. user class의 name을 가져오고 싶다!
getName()method 에서 get을 제외하고 뒤에있는 Name에서 대문자 N을 소문자 n으로 바꾼 뒤

${user.name} 

해줍니다. 
여기서 name은 class의 name을 가져오는 것이 아니라, getName() method를 통해 가져오는 것이라는 거! 

------

#####Controller는 무슨역할을 할까?

Servlet의 역할은
DB와 interface를 하고 session상태를 파악하고, jsp에 결과를 전달함.

#####View 는 뭘까?
Jsp의 역할은
완성된 결과를 보여주기만 합니다.

#####Model은 뭘까?
user를 DB에 담고, DB에서 원하는 정보를 꺼내오고 하는 logic을 담당.