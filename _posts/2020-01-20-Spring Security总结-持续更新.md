---
layout:     post
title:      Spring Security总结
subtitle:   持续更新
date:       2020-01-20
author:     BY liningwonder
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Spring Security
---


# Spring Security总结

------

应用程序的安全性主要体现在三个方面：

> * 认证：Authentication
> * 授权：Authorization
> * 审计：Audit

Spring Security作为Java应用安全领域的解决方案，提供了认证和授权两种方式的支持。

------

### 安全领域相关的概念

在安全领域有一些相关的概念，这里做统一的说明：


> * Subject：在Shiro里，Subject的实例可以表示与系统交互的用户或者程序。
> * Claims：属于JWT中的概念，也表示一个用户或程序实体
> * Principal：在Shiro中标识登录成功后的主体，可以看作是唯一标识用户的名称


### 认证技术


> * HTTP Basic认证：服务端返回401 Unauthorized，浏览器弹出对话框输入账号密码，客户端使用冒号拼接并使用Base64编码放入请求头Authorization
> * HTTP 摘要认证：
> * HTTP X.509: X.509是一种证书格式 SSL HTTPS  CA证书 Certificate Authority
> * LDAP: 轻型目录访问协议 Lightweight Directory Access Protocol
> * AD: 活动目录 Active Directory
> * OpenId:
> * CAS: Jasig Central Authentication Service
> * OAuth2.0:
> * Kerberos: The Network Authentication Protocol
> * JAAS:

### 3. 核心代码

```java
@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true)
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
  @Override
  protected void configure(HttpSecurity http) throws Exception {
    ...
  }
}
```


### 核心的类



#### 1. @EnableWebSecurity与过滤器链机制


#### 2. WebSecurityConfigurerAdapter过滤器链配置类


#### 3. 自定义过滤器OncePerRequestFilter


#### 4. 基于AuthenticationProvider的过滤

```java

ProviderManager

AuthenticationManager

AuthenticationProvider

AbstractUserDetailsAuthenticationProvider

DaoAuthenticationProdiver

UserDetails

UserDetailsService


``` 
