---
title : 배포 서술자
categories : [servlet]
tags : [servlet,spring,web.xml]
---
`배포 서술자(DD, Deployment Descriptor)`란 Java EE 스펙으로 웹 애플리케이션의 기본적인 설정을 위해 작성하는 파일이다.
JSP와 Servlet만 구성된 경우 web.xml을 배포 서술자라 한다. 파일 확장자에서 의미하는 바처럼 xml문법을 따른다.

## web.xml 주요 Element
### servlet 관련 Element
서블릿에 대한 설정
````xml
<servlet>
    <servlet-name>HelloWorldServlet</servlet-name>
    <servlet-class>com.test.HelloWorld</servlet-class>
    <descption>Hello World</descption>
</servlet>
<servlet-mapping>
    <servlet-name>HelloWorldServlet</servlet-name>
    <url-pattern>/helloworld</url-pattern>
</servlet-mapping>
````              
1. `servlet-name`
- `servlet`과 `servlet-mapping`는 `servlet-name`로 연결된다.
2. `servlet-class`
- package 경로를 포함한 실제 servlet 클래스
3. `descption` 
- 서블릿에 대한 설명 (필수값 아님)
4. `servlet-mapping`
- 내부에서 사용하는 이름과 URL 이름을 서로 매핑
5. `url-pattern`
- url 패턴에 해당하는 servlet 클래스를 찾아 호출한다.
- 와일드카드(*)도 사용 가능
(Spring MVC에서 **DispatcherServlet**을 통하여 URL 모든 요청을 적절한 Controller에 분배하기 위해 사용)

### filter 관련 Element
모든 서블릿 앞단 혹은 뒷단에 공통적으로 처리해야 할 내용
````xml
<filter>
    <filter-name>encodingFilter</filter-name>
    <filter-class>com.test.EncodingFilter</filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>UTF-8</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>encodingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
````
1. `filter-name`
- `filter`와 `filter-mapping`의 연결 servlet와 동일
2. `filter-class`
-  package 경로를 포함한 실제 filter class
3. `init-param`
- 필터 class에서 사용되는 name (`param-name`) 및 (`param-value`)
4. `servlet-mapping`, `url-pattern`
- 내부에서 사용하는 이름과 URL 이름을 서로 매핑 servlet과 동일   
