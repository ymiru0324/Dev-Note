# Tomcat

WAS(Web Application Server)

[Apache Tomcat®](https://tomcat.apache.org/index.html)

## 다운로드

홈페이지의 9.0.62 Core 버전 설치

![1](https://user-images.githubusercontent.com/81818730/167640263-f32b4432-0ef7-42df-b9cd-fa0391aa2c65.png)


### ****Source Code Distributions****

![2](https://user-images.githubusercontent.com/81818730/167640274-6ab63a77-65b9-47e5-ab3b-52523be122ba.png)


JSP 소스코드를 확인할 수 있다.

## port 설정

apache-tomcat-9.0.62\conf\server.xml

![1 1](https://user-images.githubusercontent.com/81818730/167640296-c3386d82-c464-4197-a46a-b301788b6a56.png)


port 번호 8080 → 9090으로 변경

## Tomcat Start / Stop

Start : apache-tomcat-9.0.62\bit\startup.bat

Stop : apache-tomcat-9.0.62\bit\shutdown.bat

## Eclipse 설정

Window → Preferences → Server → Runtime Environments → Add → Tomcat 버전 선택 - Create a new local server 체크 해제 → Tomcat 경로 설정

![3](https://user-images.githubusercontent.com/81818730/167640308-c49c671d-2100-4640-824a-96ea97521132.png)


→ 링크 클릭으로 서버 생성 → host name 건드리지 않고 Server name 설정

이제 Dynamic Web Project 사용 가능 !

## Dynamic Web Project

프로젝트 생성 → New → Dynamic Web Project → Project name 설정 → Tomcat 버전에 맞추어서 Dynamic Web Module Version 설정 → Target runtime Tomcat으로 설정 → *Context root

- Context root : 브라우저에 접속하게 될 이름 또는 Application name으로 context-path, context-root, application name, application alias으로 불리기도 한다

![4](https://user-images.githubusercontent.com/81818730/167640320-a5795a1b-d570-434e-92ad-310578a6757c.png)


→ 접속 후 왼쪽 하단의 Serve modules without publishing 체크 (퍼블리싱 없이 모듈을 서비스한다)
