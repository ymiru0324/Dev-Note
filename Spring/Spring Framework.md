# Spring Framework

# SpringFramework 설치 및 세팅

sts3 : Spring Legacy

sts4 : SpringBoot

Spring boot가 최신 버전이며 사용이 더 간편하지만, 아직 많은 곳에서 Spring legacy를 더 많이 사용하기에 sts3 버전을 설치하기로 한다.

[Spring Tool Suite 3 · spring-projects/toolsuite-distribution Wiki](https://github.com/spring-projects/toolsuite-distribution/wiki/Spring-Tool-Suite-3)

### JDK 1.8.0

[https://github.com/ojdkbuild/ojdkbuild](https://github.com/ojdkbuild/ojdkbuild)

### 인코딩 설정

Window → Preferences → General → Editors → Text Editors → Spelling → Default (UTF-8) 설정

Window → Preferences → General → Workspace → Other (UTF-8) 설정

Window → Preferences → Web → CSS Files → UTF-8 설정

Window → Preferences → Web → HTML Files → UTF-8 설정

Window → Preferences → Web → JSP Files → UTF-8 설정

Window → Preferences → Java → Installed JRE → JDK 1.8.0 설정

Window → Preferences → Java → Compile → JDK 1.8.0 설정

### Emmet 설정

Help → Install New Software → Work with에 [http://download.emmet.io/eclipse/updates/](http://download.emmet.io/eclipse/updates/) → 설치 → Spring 재시작 → Windows → Preferences → Emmet → jsp, java 추가

### Server 설정

Windows → Preferences → Server → Runtime Environment → 기존에 있는 서버 삭제 후 tomcat 추가

# Spring Project 생성

New → Spring Legacy Project → Project name 설정 → Spring MVC Project Templates 설정 → package를 3레벨 이상 지정해준다 ex)com.kh.spring → Finish

## Spring Project 환경 변수 설정

프로젝트 우클릭 → Properties → Java Build Path → Libraries → 현재 설정되어있는 JDK Edit 후 default JRE로 변경

프로젝트 우클릭 → Properties → Project Facets → Java 1.8

프로젝트 우클릭 → Properties → Project Facets → Dynamic Web Module 4.0

## jstl 다운로드

![2](https://user-images.githubusercontent.com/81818730/178239379-8178341c-315f-4005-a776-accc67d020c0.png)

[Apache Tomcat®](https://tomcat.apache.org/download-taglibs.cgi)

다운로드 후 src/main/webapp/WEB-INF/lib 하위에 넣어주기

## web-app/resources

js(jQuery), css, images와 같은 정적 파일이 들어간다

# Spring Project 세팅

## #1. Spring 버전 설정

### pom.xml

jdk, servlet, jsp, spring 버전 세팅

```xml
<!-- #1. java-version 1.8 / servlet 4.0.1 / jsp 2.3.1 / spring 5.1.5. RELEASE -->

	<properties>
		<java-version>1.8</java-version>
		<org.springframework-version>5.1.5.RELEASE</org.springframework-version>
		<org.springframework.security-version>5.1.5.RELEASE</org.springframework.security-version>
		<org.aspectj-version>1.6.10</org.aspectj-version>
		<org.slf4j-version>1.6.6</org.slf4j-version>
	</properties>
```

### web.xml

```xml
<!-- #1.1. web.xml 태그 설정 4.0 -->

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns="http://xmlns.jcp.org/xml/ns/javaee"
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
	id="WebApp_ID" version="4.0">
```

## #2. 전역 context 설정

### web.xml

```xml
<!-- #2. 전역 context 설정 -->

    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>/WEB-INF/spring/root-context.xml</param-value>
    </context-param>
```

## #3. DispatcherServlet 관련 context 설정

### web.xml

```xml
<!-- #3. DispatcherServlet 관련 context 설정 -->

	<servlet>
		<servlet-name>appServlet</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>/WEB-INF/spring/appServlet/servlet-context.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>

	<servlet-mapping>
		<servlet-name>appServlet</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>
```

## #4. 인코딩 설정 UTF-8 필터

### web.xml

```xml
<!-- #4. 인코딩 설정 UTF-8 필터 -->

	<filter>
		<filter-name>encodingFilter</filter-name>
		<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
		<init-param>
			<param-name>encoding</param-name>
			<param-value>utf-8</param-value>
		</init-param>
		<init-param>
			<param-name>forceEncoding</param-name>
			<param-value>true</param-value>
		</init-param>
	</filter>
	<filter-mapping>
		<filter-name>encodingFilter</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>
```

## #5. hotswapping 기능을 지원하는 의존, tomcat 구동시에 필요

### pom.xml

```xml
<!-- #5. hotswapping 기능을 지원하는 의존, tomcat 구동시에 필요 -->
<!-- jdk11 지원 안함 -->
<!-- scope : provided compile때 사용하고, 운영시 에는 사용하지 않음. -->

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>springloaded</artifactId>
			<version>1.2.8.RELEASE</version>
			<scope>provided</scope>
		</dependency>
```

## #6. boilerpate code 대신 작성. IDE에 lombok설치 필수

pom.xml에 lombok dependency 연결 후 C:\Users\사용자\.m2\repository\org\projectlombok\lombok\1.18.8 이동 후 lombok.jar 복사 스프링 깔린 곳(sts-bundle\sts-3.9.18.RELEASE)에 붙여넣기

STS.ini 파일에 javaagent:lombok경로 확인

### pom.xml

```xml
<!-- #6. boilerpate code 대신 작성. IDE에 lombok설치 필수 -->

		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<version>1.18.8</version>
			<scope>provided</scope>
		</dependency>
```

## #7. DB 영속성 관련 의존 추가

### pom.xml

```xml
<!-- #7. DB 영속성 관련 의존 추가 -->

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
			<version>${org.springframework-version}</version>
		</dependency>
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis</artifactId>
			<version>3.4.6</version>
		</dependency>
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis-spring</artifactId>
			<version>1.3.2</version>
		</dependency>
		<!-- Database Connection Pool -->
		<dependency>
			<groupId>commons-dbcp</groupId>
			<artifactId>commons-dbcp</artifactId>
			<version>1.4</version>
		</dependency>
		<dependency>
			<groupId>com.oracle.database.jdbc</groupId>
			<artifactId>ojdbc8</artifactId>
			<version>21.1.0.0</version>
		</dependency>
```

### root-context.xml

```xml
<!-- #7.1. 영속성관련 Bean 등록 -->

	<context:property-placeholder location="classpath:datasource.properties"/>
	
	<!-- datasource빈 -->
	<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
		<property name="driverClassName" value="${datasource.driverClassName}"/>
		<property name="url" value="${datasource.url}"/>
		<property name="username" value="${datasource.username}"/>
		<property name="password" value="${datasource.password}"/>
	</bean>
	<!-- sqlSessionFactory빈 -->
	<bean id="sqlSessionFactoryBean" class="org.mybatis.spring.SqlSessionFactoryBean">
		<property name="dataSource" ref="dataSource"/>
		<property name="configLocation" value="classpath:mybatis-config.xml"/>
		<property name="mapperLocations" value="classpath*:mapper/**/*-mapper.xml"/>
	</bean>
	<!-- sqlSessionTemplate빈 : SqlSession인터페이스 구현 클래스-->
	<bean id="sqlSessionTemplate" class="org.mybatis.spring.SqlSessionTemplate">
		<constructor-arg ref="sqlSessionFactoryBean"/>
	</bean>
```

## #8. Dao구현클래스 없이 mapper연결하기

### TestDao.java

```java
package com.kh.spring.test.model.dao;

import org.apache.ibatis.annotations.Mapper;

// #8. Dao구현클래스 없이 mapper연결하기

@Mapper
public interface TestDao {

}
```

### root-context.xml

```xml
<!-- #8.1. @Mapper 인터페이스를 관리 -->

	<mybatis-spring:scan base-package="com.kh.spring.member.**.dao"/>
```

### test-mapper.xml

```xml
<!-- #8.2. @Mapper인터페이스 지정 -->
<mapper namespace="com.kh.spring.test.model.dao.TestDao">
```

## #9. spring-security관련 의존

### pom.xml

```xml
<!-- #9. spring-security관련 의존 -->
<!-- 필수 core/web/config --> 

        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-core</artifactId>
            <version>${org.springframework.security-version}</version>        
        </dependency>
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-web</artifactId>
            <version>${org.springframework.security-version}</version>        
        </dependency>
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-config</artifactId>
            <version>${org.springframework.security-version}</version>        
        </dependency>

        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-taglibs</artifactId>
            <version>${org.springframework.security-version}</version>        
        </dependency>
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-test</artifactId>
            <version>${org.springframework.security-version}</version>        
        </dependency>
```

### web.xml

```xml
<!-- #9.1. root-context에 security-context.xml 설정파일 추가 -->
	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>
			/WEB-INF/spring/root-context.xml
			/WEB-INF/spring/security-context.xml
		</param-value>
		<!-- <param-value>/WEB-INF/spring/*-context.xml</param-value> -->
		<!-- 이것 또한 가능하다-->
	</context-param>
```

### security-context.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

	<!-- #9.2. bcryptPasswordEncoder빈 등록 -->
	<bean id="bcryptPasswordEncoder" class="org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder"/>
</beans>
```
