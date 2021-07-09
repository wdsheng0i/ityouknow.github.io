---
layout: post
title: 单体架构-技术选型
category: arch
tags: [arch]
---

单体架构-技术选型

## 一、前端框架
Requirejs：动态资源加载，模块化定义与加载  
bootstrap：响应式栅布局  
Freemarker：模板+数据 后端渲染  

- html + js + css + jquery + bootstrap +  Requirejs  
- jsp+ js + css + jquery + bootstrap +  Requirejs
- vue.js 技术栈    
- angular.js 技术栈  
- react.js 技术栈  

## 二、前后交互
- 集中部署: tomcat  
AJAX请求,  JSON交互数据
- 前后分离部署：  tomcat + nginx  
nginx做LB
AJAX请求,  JSON交互数据

## 三、 后端框架（SSM）
- Controller层使用适配器 
- Service层很常规   
- dao层使用JPA简化开发   mybatis + tk.mybatis +PageHelper
- 连接池：使用dbcp2、druid、c3p0
- 缓存：使用ehcache、redis缓存：
- 热数据：mongodb
- 全文检索：ES
- 定时任务：  spring定时任务
- 线程任务：线程池用来执行task
- 统一异常处理：aop
- 日志处理：aop
- 事务处理：spring事务
- 消息队列：rocketmq
- 安全，登录验证：sso、shiro、token、session、状态、login
- 组织机构，权限：uim、sso
- 服务交互接口：（Websevice、RestfulHttp、dubbo）
- 规范开发：清晰合理的包结构  
```
api
base
cache
common
    utils
    const
interceptor
filter
config
threadtask
timetask
controller
service
mapper
entity/model/pojo
```

## 四、存储选型
- 结构化存储：  
数据库 Oracle、Mysql、postgresql、SqlServer

- 非结构化存储：  
文件服务 FTP、Minio、ElasticSearch、OSS

## 五、 服务器
- 服务器：Linux/WindowServer

- 服务器中间件：Tomact/Jetty/Jboss







