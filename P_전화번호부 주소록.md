# 전화번호부 주소록

---

간단하게 전화번호부 기능이 들어가있는 웹 프로젝트

**간단 명료**한 **기본 기능**에 충실한 프로젝트이며

파이썬 언어와, 플라스크 프레임워크를 사용한 것에 의의를 두었다.



## 작업 환경

운영체제 : macOS 10.15, Windows 10

사용언어 : Python v3.7.7, virtual evironment

사용 프레임워크 : Flask v1.1.2

사용 에디터 : Visual Studio Code v1.45.0

사용 DB : SQLite3



## DB설계

index - PRIMARY KEY, NUMBER, 

name - TEXT

phone - TEXT



## 참고 사이트

화면 디자인 - https://www.miricanvas.com/

플라스크 공식 사이트 - https://flask-docs-kr.readthedocs.io/ko/latest/



## 작업 기간

작업 기간 : 2020/05/09 ~ 2020/05/10 (2일)



## 화면 구성

#### 메인화면 

![image-20200512172807548](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200512172807548.png)

간단하게 나의 전화번호부의 리스트를 보여주며 검색기능과 새롭게 연락처를 추가하는 기능을 넣었다.

![image-20200512173007071](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200512173007071.png)

![image-20200512172937730](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200512172937730.png)

검색시 리스트에 연락처가 있는경우 연락처가 검색이 되고, 연락처가 없을시에 새롭게 추가하는 팝업 창을 넣었다.



#### 전화번호부 상세보기

![image-20200512173208944](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200512173208944.png)

연락처 상세보기 화면. 뒤로 가면 메인화면이 나오고 수정을 누를시 수정할수 있는 화면으로 넘어간다.



#### 전화번호부 수정

![image-20200512173320503](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200512173320503.png)

![image-20200512173335475](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200512173335475.png)

사용자는 연락처를 수정할수 있고, 삭제할 시에 실수로 삭제 버튼을 누를 수도 있는 경우가 발생할수 있기에 다시한번 사용자에게 물어보는 팝업 창을 구현 하였다.



## 코드페이지

git : https://github.com/yksoon/Project_contact_flask

코드는 git주소로 대신 하면 될 것 같고 오류생긴 코드가 있을 경우만 참고하면 좋을 것 같습니다.



## 프로젝트를 진행하며 느낀점

간단한 소규모 프로젝트를 진행하게 된 주된 목적은 파이썬과 Flask 프레임워크를 사용경험을 해보는 것이었다.

사용자는 간단 명료하게 사용할수 있고, 심플한 디자인을 추구 하였으며, 프로젝트를 진행하며 Flask 프레임워크의 전반적인 흐름을 알 수 있는 좋은 계기가 되었다.



## 프로젝트를 진행하며 힘들었던 점

학원에서 배운 강의 내용을 토대로 프로젝트를 진행 하였다. Flask 프레임워크를 심도 있게 배운 것이 아니었기 때문에 그동안 공부 했던 MVC기반으로 이해하여 구성하려 하였다.

디자인 부분에서는 많은 재능이 있지 않아 화면을 심플하게 만드는데 어려움이 있었다.

- 해결책 :

  Flask 관련 구글링 검색과 공식 사이트 등을 활용하였고, 모르는 점은 학원 강사에게 질문하여 해결을 하였고, 디자인적 측면에서는 참고사이트에서 전반적인 디자인 템플릿을 만들어 사용했다.



## 발전하기 위한 방향

Flask를 사용하는데 의의를 두어 많은 기능이 있지 않다. 조금더 대규모 프로젝트를 접하게 된다면 많은 연구와 공부가 필요할 것 같고, 이를 위해 개인적으로 소규모 프로젝트를 몇개 더 진행해 보는것이 좋을 것 같다.