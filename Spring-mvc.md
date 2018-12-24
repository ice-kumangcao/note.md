[TOC]

## Spring MVC 5.0.2框架

### web.xml

```xml
<!-- contextLoaderListener初始化数据 -->    
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>WEB-INF/spring-mvc.xml</param-value>
</context-param>
<listener>
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
<servlet>
    <servlet-name>main</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <!-- main Servlet初始化数据，默认文件为main-Servlet.xml -->
    <init-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>WEB-INF/spring-mvc.xml</param-value>
    </init-param>
    <load-on-startup>1</load-on-startup>
</servlet>
<servlet-mapping>
    <servlet-name>main</servlet-name>
    <url-pattern>/</url-pattern>
</servlet-mapping>
```

