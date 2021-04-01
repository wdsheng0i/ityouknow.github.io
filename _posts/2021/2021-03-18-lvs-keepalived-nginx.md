---
layout: post
title: LVS + keepalived + Nginx实现负载均衡、高可用集群
category: arch
tags: [arch]
---

LVS + keepalived + Nginx实现负载均衡、高可用集群

## 搭建高可用集群负载均衡
## 1 LVS简介  

## 2 为什么要使用 LVS + Nginx？ 
 
## 3 LVS的三种模式  

## 4-5 搭建LVS-DR模式- 配置LVS节点与ipvsadm 

## 6-7 搭建LVS-DR模式- 为两台RS配置虚拟IP 

## 8-9 搭建LVS-DR模式- 为两台RS配置arp 

## 10-11 搭建LVS-DR模式- 使用ipvsadm配置集群规则  

## 12 搭建LVS-DR模式- 验证DR模式，探讨LVS的持久化机制 

## 13 搭建Keepalived+Lvs+Nginx高可用集群负载均衡 - 配置Master  

## 14 搭建Keepalived+Lvs+Nginx高可用集群负载均衡 - 配置Backup 

## 15 附：LVS的负载均衡算法
单个nginx往往是不够的，因为他的并发量还是有限，所以很多企业会采用LVS，LVS是四层负载，LVS涉及到NAT|TUN|DR这三种模式，我们也讲了他们
原理，并且实现了DR模式，当然，为了保证LVS的高可用，咱们也配合使用了Keepalived，因为Keepalived可以说就是为lvs量身打造的。需要注意，当keepaliv
以后，nginx作为lvs的集群，就无需和keepalived结合了。