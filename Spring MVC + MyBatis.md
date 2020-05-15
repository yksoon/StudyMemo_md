# Spring MVC + MyBatis



## 주제 : 게시물 관리



## 작업순서

1. 요구분석(요구사항)
2. 개발환경 구축
3. 플랫폼 구축
4. Database 테이블
5. Database 연결 데스트
6. 영속 계층 테스트
7. 비즈니스 계층 테스트

## 1. 요구분석 : CRUD기능 구현

## 2. 개발환경 구축

- jdk 1.8
- Oracle 11g XE
- Tomcat 5.0
- eclipse + STS Plug-in
- MyBatis Plug-in
- Workspace Encoding 설정

## 3. 플랫폼 구축 : pom.xml

Maven을 통한 버전 관리

- Spring 5.3
- Java 1.8
- Log4J / JUnit
- Hikari
- Mybatis-spring

## 4. Database 테이블

Oracle

tbl_board

- bno : primary key(Number)
- title : varchar2
- content : varchar2
- writer : varchar2
- regdate : Date(default sysdate)
- updateDate : Date(default sysdate)

