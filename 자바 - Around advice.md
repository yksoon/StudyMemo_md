# Around advice

**Around Advice (특정 메소드 기준 실행)**

**Around advice**는 **Before**와 **After** 위치를 둘 다 지정해 줄 수 있다.



![image-20200521091645351](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200521091645351.png)

> Around advice를 사용할 Class 생성

일반 Advice와 구현받는 interface가 다르다.

Around advice 는 MethodInterceptor 를 구현받는다.

```java
/SpringAOP2/src/main/java/sp/aop/BALogAdvice.java

package sp.aop;

import org.aopalliance.intercept.MethodInterceptor;
import org.aopalliance.intercept.MethodInvocation;

// 3. Around Advice 를 구현 -> MethodInterceptor 를 상속
// 자동으로 invoke()를 호출한다. -> 앞, 뒤에 공통으로 실행할 내용을 기술하게 되어있다.
// 핵심 Class 의 Method 호출 -> MethodInvocation 객체명.proceed() 이용해서 호출한다.

public class BALogAdvice implements MethodInterceptor {

	@Override
	public Object invoke(MethodInvocation invocation) throws Throwable {
		// TODO Auto-generated method stub
		
		// Class 호출 전
		// invacation.getMethod() 핵심 Class 의 Method 이름을 구해 온다.
		System.out.println("invoke() 호출 됨!");
		System.out.println(invocation.getMethod() + "호출 전인 경우");
		
		// 핵심 Class의 Method 호출
		Object returnValue = invocation.proceed();
		
		// Class 호출 후
		System.out.println(invocation.getMethod() + "호출 후인 경우");
		
		System.out.println(returnValue + "returnValue 를 Return!");
		return null;
	}

}
```

```xml
/SpringAOP2/src/main/java/sp/aop/app.xml

<!-- 2. Advice Class 빈즈 등록 -->
<bean id="beforeLog" class="sp.aop.BeforeLogAdvice" />
<bean id="AfterLog" class="sp.aop.AfterLogAdvice" />
<bean id="BALog" class="sp.aop.BALogAdvice"></bean>	<!-- 추가 -->

<!-- 4. Advice + PointCut(Advisor) 설정 -->
<bean id="testAdvisor" class="org.springframework.aop.support.DefaultPointcutAdvisor">
   <property name="advice" ref="beforeLog" />
   <property name="pointcut" ref="writePointcut" />
</bean>

<bean id="testAfterAdvisor" class="org.springframework.aop.support.DefaultPointcutAdvisor">
   <property name="advice" ref="AfterLog" />
   <property name="pointcut" ref="savePointcut" />
</bean>

<!-- 추가 -->
<bean id="testBAAdvisor" class="org.springframework.aop.support.DefaultPointcutAdvisor">
   <property name="advice" ref="BALog" />
   <property name="pointcut" ref="writePointcut" />
</bean>		

<!-- 5. AOP를 적용(ProxyFactoryBean 객체를 생성) target(핵심 Class) -->
<bean id="testService" class="org.springframework.aop.framework.ProxyFactoryBean">
   <property name="target" ref="testServiceImpl" />
   <property name="interceptorNames">
      <list>
         <value>testAdvisor</value>
         <value>testAfterAdvisor</value>
         <value>testBAAdvisor</value>	<!-- 추가 -->
      </list>
   </property>
</bean>
```

```xml
/SpringAOP2/src/main/java/sp/aop/app.xml

<!-- 3.PointCut 생성 -> 어느 위치에서 AOP Method 를 지정해서 실행
   value="접근 지정 반환명 package 명... Class 명 하위  package 명(..) 특정 Method명 0개 이상"
           (*) 매개변수 한 개 표시, (*,*) 매개변수 2개 표시 -->
           
<bean id="writePointcut" class="org.springframework.aop.support.JdkRegexpMethodPointcut">
   <property name="patterns">
   		<list>
   			<value>.*write.*</value>
   			<value>.*save.*</value>
   		</list>
   </property>
</bean>
```

> 다중 포인트컷은 이렇게 합칠 수 있다.  다만 `<property name="patterns">`patterns로 수정하는것도 잊지 말자



## web에서의 AOP : xml 스키마 기반 AOP 퀵스타트 방법

AOP를 실행시키는 방법

1. 프록시 기반의 AOP를 지원 (Aop 객체를 생성해주는 Class)

   default(Method 중심) -> 빈즈 Class로 구성

2. `<aop:config>` 태그를 이용

3. AspectJ 이용 (@Aspect Annotation 을 이용하는 방법)

```xml
/SpringAOP/pom.xml

<!-- 추가 aop:aspect -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.7.4</version>
</dependency>
```

![image-20200521110433234](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200521110433234.png)

### Web project 설정 계획

핵심 모듈(Class) -> Method(핵심기능)

공통 모듈(Class) : advice -> Method

DTO, DAO 부분 (Model) -> Method(핵심기능)



### 새로운 Class 생성

![image-20200521110855757](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200521110855757.png)

```java
/SpringAOP/src/main/java/com/yks/medel/MyModel.java

package com.yks.model;

// 핵심 Class (=Target Class) -> Method -> Controller 호출

public class MyModel {
	
	public String processMsg() {
		System.out.println("핵심 기능 실행됨!");
		return "Spring Web AOP 연습";
	}

}
```



### 공통 모듈 생성

![image-20200521111627291](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200521111627291.png)

```java
/SpringAOP/src/main/java/com/yks/security/SecurityClass.java

package com.yks.security;

// 공통 모듈 클래스

public class SecurityClass {
	
	public void security() {
		System.out.println("핵심 내용을 보기 전에 보안 작업 실행!");
	}

}
```



### aspect 클래스 생성

![image-20200521112155742](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200521112155742.png)

```java
/SpringAOP/src/main/java/com/yks/aspect/MyAspectBean.java

package com.yks.aspect;

import com.yks.security.SecurityClass;

public class MyAspectBean {
	
	// 1. 메소드 호출 전 -> Security Class -> Security()
	public void beforeProcess() {
		SecurityClass class1 = new SecurityClass();
		class1.security();
	}
	
	// 2. 메소드 호출 후
	public void afterProcess() {
		System.out.println("핵심 내용 후에 실행될 Method");
	}

}
```



```
MyModel.java
	└─ processMSG(){}	//핵심기능
SecurityClass.java
	└─ security(){}
MyAspectBean.java
	└─ beforeProcess(){}
	└─ afterProcess(){}
```

> 현재까지 구조



### Controller 구현

```java
/SpringAOP/src/main/java/com/yks/controller/TestController.java

package com.yks.controller;

import org.springframework.stereotype.Controller;

import com.yks.model.MyModel;

// /hello.do 요청이 들어왔을 시 -> TestController 실행 -> 출력 문자열 출력
@Controller
public class TestController {	// @Controller 사용으로 인하여 POJO Class가 됨
	
	// MyModel 객체를 얻어와야 함 import com.yks.model; or xml에서 설정
	private MyModel model;
	
	// DI
	public void setModel(MyModel model) {
		this.model = model;
		System.out.println("setModel() 호출됨!");
	}

}
```



### web.xml 수정

```xml
/SpringAOP/src/main/webapp/WEB-INF/web.xml

<display-name>SpringBoard</display-name>	// 추가
<servlet>
    <servlet-name>board</servlet-name>		// 수정
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <init-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>/WEB-INF/spring/appServlet/servlet-context.xml</param-value>
    </init-param>
    <load-on-startup>1</load-on-startup>
</servlet>

<servlet-mapping>
    <servlet-name>board</servlet-name>	// 수정
    <url-pattern>*.do</url-pattern>		// 수정
</servlet-mapping>
```



### servlet-context 추가

```xml
/SpringAOP/src/main/webapp/WEB-INF/spring/appServlet/servlet-context.xml

<beans:beans xmlns="http://www.springframework.org/schema/mvc"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:beans="http://www.springframework.org/schema/beans"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:p="http://www.springframwork.org/schema/p"	// 추가
	xmlns:aop="http://www.springframwork.org/schema/aop"	//추가
	xsi:schemaLocation="http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd
		http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">
```

