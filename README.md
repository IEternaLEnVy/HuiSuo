# HuiSuo
软件工程健康会所管理系统
在初期，养生会所的管理主要采用手工纸笔记录的方式，
这种管理模式繁琐，对于管理者要求高，人工成本也随之提高，
随着互联网和PC的发展普及，如同众多管理系统，
养生会所管理系统也随之诞生。
市场上也有许多同类产品，管理系统的诞生提高了管理的效率，
极大降低了人工失误带来的损失，
节约了人工成本，管理系统本着提高效率，简单易用的目标。
此项目参考了目前市场上诸多同类产品，
结合实际要求，力求实现管理的简洁化。
    

系统开发环境
系统                windows10
java环境          JDK1.8
IDE                  Eclipse10
数据库             Mysql5.6
数据库管理      Navicat
版本仓库         GitHub
web服务器      Tomcat9.0
远程服务器     CloudStation




当下最主流的web项目框架SSM框架是spring MVC ，
spring和mybatis框架的整合，
是标准的MVC模式，将整个系统划分为表现层
，controller层，service层，DAO层四层
使用spring MVC负责请求的转发和视图管理
spring实现业务对象管理，mybatis作为数据对象的持久化引擎



driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql://127.0.0.1:3306/grogshop?useUnicode=true&characterEncoding=utf-8
username=root
password=496520
validationQuery=SELECT 1



<?xml version="1.0" encoding="UTF-8"?>

-<beans xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.1.xsd http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.1.xsd http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-3.1.xsd" xmlns:context="http://www.springframework.org/schema/context" xmlns:p="http://www.springframework.org/schema/p" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:mvc="http://www.springframework.org/schema/mvc" xmlns="http://www.springframework.org/schema/beans">

<!-- 自动扫描controller包下的所有类，使其认为spring mvc的控制器 -->



-<context:component-scan base-package="com.gx.web">

<context:include-filter expression="org.springframework.stereotype.Controller" type="annotation"/>

</context:component-scan>

<!-- 日期转换 必须放在<mvc:annotation-driven />前面 -->


<bean class="org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter"/>


-<mvc:annotation-driven>


-<mvc:message-converters>


-<bean class="org.springframework.http.converter.StringHttpMessageConverter">


-<property name="supportedMediaTypes">


-<list>

<value>application/json;charset=UTF-8</value>

<value>application/x-www-form-urlencoded;charset=UTF-8</value>

</list>

</property>

</bean>

</mvc:message-converters>

</mvc:annotation-driven>

<!-- 启动Spring MVC的注解功能，完成请求和注解POJO的映射 -->


<bean class="org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter"/>

<!-- 对模型视图名称的解析，即在模型视图名称添加前后缀 -->



-<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">

<property name="prefix" value="/WEB-INF/jsp"/>

<property name="suffix" value=".jsp"/>

</bean>

<!-- 定义文件上传解析器 -->



-<bean class="org.springframework.web.multipart.commons.CommonsMultipartResolver" id="multipartResolver">

<!-- 设定默认编码 -->


<property name="defaultEncoding" value="UTF-8"/>

<!-- 设定文件上传的最大值5MB，5*1024*1024 -->


<property name="maxUploadSize" value="5242880"/>

</bean>

</beans>
