---
layout: post
title: 《大数据开发工程师》课程目录-【慕课网】
category: big-data
tags: [big-data]
---

## 资料
- [快速入门Hadoop3.0大数据处理-【慕课网】](https://www.imooc.com/learn/1159)  
- [大数据开发工程师-【慕课网】](https://class.imooc.com/sale/bigdata) 
- 官网：https://hadoop.apache.org 
- Hadoop文档: http://hadoop.apache.org/docs/r1.0.4/cn/index.html  
- 《HADOOP权威指南》  
- [史上最详细的Hadoop环境搭建](https://blog.csdn.net/hliq5399/article/details/78193113/)  
- [使用docker搭建hadoop分布式集群](https://blog.csdn.net/xu470438000/article/details/50512442)  

## 阶段一：走进大数据  
![](../../assets/images/2021/big-data/big-data.png)

### 第1周   学好大数据先攻克Linux  
1、掌握Linux虚拟机的安装和配置  
2、使用ScecureCRT连接Linux虚拟机  
3、掌握Linux中常见高级命令(vi、wc、sort、date、jps、kill等命令)的使用  
4、掌握Linux中三剑客(grep、sed、awk)的常见用法  
5、掌握Linux的高级配置(ip、hostname、防火墙)  
6、掌握Shell脚本的开发  
7、掌握Shell中变量、循环和判断的使用  
8、掌握Shell中的扩展内容  
9、掌握Linux中crontab定时器的使用  
10、了解认识什么是大数据  
11、大数据产生的背景  
12、大数据的4V特征  
- Volume（大量）、
- Velocity（高速）、
- Variety（多样）： 结构型的数据，也可能是非结构行的文本，图片，视频，语音，日志，邮件等
- Value（低价值密度）、
- Veracity（真实性）

13、大数据的行业应用  
  
### 第2周   大数据起源之初识Hadoop  
1、什么是[Hadoop](https://baike.baidu.com/item/Hadoop/3526507?fr=aladdin)  
PB级别海量数据存储和计算的平台;  
Hadoop是由java语言编写的，在分布式服务器集群上存储海量数据并运行分布式分析应用的开源框架，其核心部件是HDFS与MapReduce。  

1-2、Hadoop能干什么   
[Hadoop到底是干什么用的？](https://www.zhihu.com/question/333417513)    
https://blog.csdn.net/qq_32649581/article/details/82892861    
Hadoop是专为离线和大规模数据分析而设计的，并不适合那种对几个记录随机读写的在线事务处理模式。   
- 大数据存储：分布式存储
- 日志处理：擅长日志分析 (实际应用：Flume+Logstash+Kafka+Spark Streaming进行实时日志处理分析)
- ETL:数据抽取到oracle、mysql、DB2、mongdb及主流数据库
- 机器学习: 比如Apache Mahout项目
- 搜索引擎:Hadoop + lucene实现
- 数据挖掘：目前比较流行的广告推荐，个性化广告推荐

2、Hadoop发行版介绍：   
- 官方版本：Apache hadoop，开源，集群、安装维护较麻烦
- CDH版本：Cloudera hadoop，商用版本，部分功能开源，使用cloudera Manager 安装维护方便
- HDP版本：HortonWorks，开源，使用Ambari安装维护方便

3、Hadoop版本演变历史    
1.X -> 2.X -> 3.X 
![](../../assets/images/2021/big-data/hadoop-v.png)

4、Hadoop3.x的细节优化  

5、Hadoop三大核心组件介绍 
- HDFS: （海量数据）分布式数据存储, HDFS理解为一个分布式的，有冗余备份的，可以动态扩展的用来存储大规模数据的大硬盘。
- MapReduce: （海量数据）分布式计算, MapReduce理解成为一个计算引擎，按照MapReduce的规则编写Map计算/Reduce计算的程序，可以完成计算任务。
- Yarn: 集群资源管理, 能监控服务器的资源使用，分配跟踪程序运行；    

6、伪分布（一台虚拟机）集群安装部署 
```
1.环境准备
    ip设置
    主机名设置（临时+永久）
    hosts文件修改（ip和主机名的映射关系）
    关闭防火墙（临时+永久）
    ssh免密登录
    jdk安装
2.下载: https://hadoop.apache.org/releases.html
3.上传、解压
4.配置修改

5.shell脚本修改
    start-dfs.sh
    stop-dfs.sh
    start-yarn.sh
    stop-yarn.sh
6.启动
7.查看进程、浏览器访问
8.停止
``` 

7、分布式（3台虚拟机）集群安装部署 
```
1.环境准备:没台机器都需要
    ip设置
    主机名设置（临时+永久）
    hosts文件修改（ip和主机名的映射关系）：需要配置3台的
    关闭防火墙（临时+永久）
    ssh免密登录：除了各自自身免密登录外，还要实现主节点免密登录从节点,想实现100这个节点免密码登录到101和102所以需要把100的公钥拷贝到101和102
    jdk安装
2.下载: https://hadoop.apache.org/releases.html
3.上传、解压
4.配置修改

5.shell脚本修改
    start-dfs.sh
    stop-dfs.sh
    start-yarn.sh
    stop-yarn.sh
6.启动
7.查看进程、浏览器访问
8.停止
```
 
8、Hadoop的客户端节点  
直接操作集群节点是不安全的，所以一般在业务机上安装hadoop客户端，再业务机上操作hadoop集群  
   
### 第3周   Hadoop之HDFS（hadoop distributed file system）的使用  
![](../../assets/images/2021/big-data/hdfs.png)  
1、Hadoop中的分布式存储架构 -- 生活场景引入：”小明租房”案例一步一步引入    
HDFS是一种允许文件通过网络在多台主机上分享的文件系统，可以让多机器上多用户分享文件和存储空间;  
- 通透性
- 容错性
- 不适合存储小文件

HDFS支持主从结构：
- 主节点支持多个NameNode；从节点支持多个DataNode
- NameNode负责接受读写请求、维护目录系统结构；DataNode负责存储数据  
  
2、HDFS的Shell介绍  
- 使用格式: bin/hdfs dfs -xXx schema://authority/ path
- HDFS的schema是hdfs, authority是NameNode的节点ip和对应的端口号，path是我们要操作的路径信息

3、HDFS的常见Shell操作  
- -Is: 查询指定路径信息
- -get: 下载文件到本地
- -put: 从本地.上传文件
- -mkdir [-p]:创建文件夹
- -cat: 查看HDFS文件内容◆ -rm [-r]: 删除文件/文件夹

4、HDFS案例实操  

5、Java代码操作HDFS  

6、HDFS的高级Shell命令  

7、HDFS读数据过程分析  

8、HDFS写数据过程分析  

9、HDFS写数据源码分析  
   
### 第4周   Hadoop之HDFS核心进程剖析  
![](../../assets/images/2021/big-data/node-struct.png)  

1、NameNode介绍   
1.1 主要包含以下文件：  
- fsimage（内存数据快照）、
- edits（修改操作记录）、
- seed_txid（事务id即edits的id）、
- version（版本信息）

1.2 维护两份关系
- 第一份关系file与block list关系，存储在fsimage、edits中
- 第二份关系dataNode和block关系，dataNode启动时，会把当前节点信息+节点上block信息 上报给NameNode

2、NameNode（主节点上）深入  

3、SecondaryNameNode（主节点上）介绍  
- 主要负责把edits文件的内容合并到fsimage中
- 这个合并操作成为checkpoint，合并时会对edits内容进行转换，生成新的内容保存到fsimage中
- 注意：在nameNode的HA架构中是没有SecondaryNameNode进程的，这时文件合并操作时由standby NameNode负责实现的

4、DataNode（从节点上）介绍  
- 提供真实文件数据存储服务
- hdfs会按照固定大小顺序对文件进行编号，划分的每一块block，默认大小128M
- 如果一个数据块大小小于128M，不会占用整个数据block

5、HDFS的回收站  

6、HDFS的安全模式详解 
 
7、实战：定时上传数据至HDFS  

8、HDFS的高可用和高扩展机制分析  
   
### 第5周   Hadoop之初识MR  
1、MapReduce介绍  
MapReduce是一个分布式计算模型，主要负责海量数据计算，主要有两个阶段组成：map和reduce  
- Map阶段是一个独立程序，会在很多节点同时执行，每个节点处理一部分数据
- Reduce阶段也是独立程序，可以理解为一个单独的聚合程序
- 框架有默认实现，用户只需要覆盖map()和reduce()两个函数，即可实现分布式计算

2、MapReduce执行原理  
![](../../assets/images/2021/big-data/map-reduce.png)    
![](../../assets/images/2021/big-data/map-reduce-2.png)  

2-2、shuffle过程分析  
![](../../assets/images/2021/big-data/shuffle.png)   
框架对多个map任务的输出，按照不同的分区，通过网络copy到不同的reduce节点，这个过程称作shuffle

3、实战：WordCount案例图解 
![](../../assets/images/2021/big-data/word-count.png)  
![](../../assets/images/2021/big-data/word-count2.png)  
![](../../assets/images/2021/big-data/word-count3.png)

4、实战：WordCount案例开发 
 
5、MapReduce任务日志查看   
开启yarn的日志聚合功能，把散落在nodemanager节点上的日志收集管理:   
- 修改yarn-site.xml中<yarn.log-aggregation-enable>和<yarn.log.server.url>
- 重启集群：sbin/start.sh
- 启动history进程(每个节点都要)：sbin/mr-jobhistory-daemon.sh start historyserver
- 浏览器查看任务history

6、停止Hadoop集群中的任务  
查看任务：yarn application -list
停任务：yarn application -kill {application_id}

7、MapReduce程序扩展

7-2、hsdoop序列化机制介绍   
![](../../assets/images/2021/big-data/xlh.png)
hadoop序列化机制的特点
- 紧凑：高效使用空间
- 快速： 读写数据额外开销小
- 可扩展：可透明读取老格式数据
- 互操作：支持多语言的交互
   
## 阶段二：PB级离线数据计算分析方案  
### 第6周   拿来就用的企业级解决方案  
1、小文件问题之SequenceFile  

2、小文件问题之MapFile  

3、案例：小文件存储和计算 
 
4、 数据倾斜问题分析  

5、数据倾斜案例实战 
 
6、YARN资源调度器介绍  
主要负责集群资源的管理和调度，支持主从结构  
![](../../assets/images/2021/big-data/yarn.png)  
- 主节点（ResourceManager）进程主要负责集群资源的管理和分配,并处理客户端请求,启动和监控AppMaster,NodeManager  
- 从节点（NodeManager）主要负责单节点资源管理,处理ResourceManager,AppMaster 的命令 
- AppMaster：负责某个具体应用程序的调度和协调,为应用程序申请资源,并对任务进行监控
- Container：YARN中的一个动态资源分配的概念，其拥有一定的内存，核数 

7、YARN中的调度器分析   
![](../../assets/images/2021/big-data/yarn-schedule.png)  
- FIFO Scheduler:先进先出(first in, first out)调度策略
- CapacityScheduler:可以看作是FifoScheduler的多队列版本。
- FairScheduler:多队列，多用户共享资源。
 
8、案例：YARN多资源队列配置和使用 
 
9、Hadoop官方文档使用指北
  
10、Hadoop在CDH中的使用  

11、Hadoop在HDP中的使用  
   
### 第7周   Flume从0到高手一站式养成记   
1、快速了解Flume  

2、Flume的三大核心组件  

3、Flume安装部署  

4、Flume的Hello World  

5、案例：采集文件内容上传至HDFS  

6、Flume高级组件之Source Interceptors  

7、Flume高级组件之Channel Selectors  

8、Flume高级组件之Sink Processors  

9、各种自定义组件  

10、Flume优化  

11、Flume进程监控  

  
### 第8周   数据仓库Hive从入门到小牛  
1、快速了解Hive  

2、数据库和数据仓库的区别  

3、Hive安装部署  

4、Hive使用方式之命令行方式  

5、Hive使用方式之JDBC方式  

6、Set命令的使用  

7、Hive的日志配置  

8、Hive中数据库的操作  

9、Hive中表的操作  

10、Hive中数据类型的应用  

11、Hive表类型之内部表+外部表  

12、Hive表类型之内部分区表  

13、Hive表类型之外部分区表  

14、Hive表类型之桶表+视图  

15、Hive数据处理综合案例  

16、Hive高级函数之分组排序取TopN  

17、Hive高级函数之行转列  

18、Hive高级函数之列转行  

19、Hive的排序函数  

20、Hive的分组和去重函数  

21、一个SQL语句分析  

22、Hive的Web工具-HUE  

  
## 阶段三：Spark+综合项目：电商数据仓库设计与实战  
### 第9周   7天极速掌握Scala语言   
1、快速了解Scala  

2、Scala环境安装配置  

3、Scala中的变量和数据类型  

4、Scala中的表达式和循环  

5、Scala集合体系之Set+List+Map  

6、Scala中的Array和Tuple  

7、Scala中函数的使用  

8、Scala面向对象之类的使用  

9、Scala面向对象之对象和伴生对象  

10、Scala面向对象之apply和main的使用  

11、Scala面向对象之接口的使用  

12、Scala函数式编程之匿名函数和高阶函数的使用  

13、Scala高级特性之模式匹配和隐式转换  

  
### 第10周   Spark快速上手   
1、快速了解Spark  

2、Spark 集群安装部署(Standalone+ON YARN)  

3、Spark工作原理分析  

4、什么是RDD  

5、Spark架构原理  

6、Spark项目开发环境配置  

7、WordCount代码开发(Java+Scala)  

8、Spark任务的三种提交方式  

9、Spark开启historyServer服务  

10、创建RDD的三种方式  

11、Transformation和Action介绍  

12、Transformation操作开发实战  

13、Action操作开发实战  

14、RDD持久化原理  

15、RDD持久化开发实战  

16、共享变量之Broadcast Variable的使用  

17、共享变量之Accumulator的使用  

18、案例实战：TopN主播统计  

19、面试题  

  
### 第11周   Spark性能优化的道与术   
1、宽依赖和窄依赖  

2、Stage的理解  

3、Spark任务的三种提交模式  

4、Shuffle介绍  

5、三种Shuffle机制分析  

6、checkpoint概述  

7、checkpoint和持久化的区别  

8、checkpoint代码开发和执行分析  

9、checkpoint源码分析之写操作和读操作  

10、Spark程序性能优化分析  

11、高性能序列化类库Kryo的使用  

12、持久化或者checkpoint  

13、JVM垃圾回收调忧  

14、提高并行度  

15、数据本地化  

16、算子优化  

17、SparkSql快速上手使用  

18、实战：SparkSQL实现TopN主播统计  

  
### 第12周   综合项目：电商数据仓库之用户行为数仓   
1、项目效果展示  

2、项目的由来  

3、什么是数据仓库  

4、数据仓库基础知识  

5、数据仓库分层  

6、典型数仓系统架构分析  

7、技术选型  

8、整体架构设计  

9、服务器资源规划  

10、生成用户行为数据【客户端数据】  

11、生成商品订单相关数据【服务端数据】  

12、采集用户行为数据【客户端数据】  

13、Sqoop安装部署  
![](../../assets/images/2021/big-data/sqoop1.png)  
![](../../assets/images/2021/big-data/sqoop2.png)

14、Sqoop之数据导入功能  

15、Sqoop之数据导出功能  

16、采集商品订单相关数据【服务端数据】  

17、用户行为数据数仓开发之ods层开发  

18、用户行为数据数仓开发之ods层脚本抽取  

19、用户行为数据数仓开发之dwd层开发  

20、用户行为数据数仓开发之dwd层脚本抽取  

21、用户行为数据数仓需求分析  

22、用户行为数据数仓需求开发  

23、用户行为数据数仓表和任务脚本总结  

  
### 第13周   综合项目：电商数据仓库之商品订单数仓   
1、商品订单数据数仓开发之ods层和dwd层  

2、商品订单数据数仓需求分析与开发  

3、什么是拉链表  

4、如何制作拉链表  

5、【实战】基于订单表的拉链表实现  

6、拉链表的性能问题分析  

7、商品订单数据数仓表和任务脚本总结  

8、数据可视化之Zepplin的安装部署和参数配置  

9、数据可视化之Zepplin的使用  

10、任务调度之Crontab调度器的使用  

11、任务调度之Azkaban的安装部署  

12、任务调度之Azkaban提交独立任务  

13、任务调度之Azkaban提交依赖任务  

14、任务调度之在数仓中使用Azkaban  

15、项目优化  

  
## 阶段四：高频实时数据处理方案  
### 第14周   消息队列之Kafka从入门到小牛   
1、什么是消息队列  

2、什么是Kafka  

3、Zookeeper安装部署之单机模式和集群模式  

4、 Kafka安装部署之单机模式和集群模式  

5、Kafka中的生产者和消费者  

6、案例：QQ群聊天  

7、Broker扩展内容  

8、Producer扩展内容  

9、Consumer扩展内容  

10、Topic+Partition+Message扩展内容  

11、Kafka中的存储策略  

12、Kafka中的容错机制  

13、Java代码实现生产者代码  

14、Java代码实现消费者代码  

15、消费者代码扩展  

16、Consumer消费Offset查询  

17、Consumer消费顺序  

18、Kafka的三种语义  

19、Kafka参数调忧之JVM参数调忧  

20、Kafka参数调忧之Replication参数调忧  

21、Kafka参数调忧之Log参数调忧  

22、Kafka Topic命名小技巧  

23、Kafka集群监控管理工具(CMAK)  

24、实战：Flume集成Kafka  

25、实战：Kafka集群平滑升级  

  
### 第15周   极速上手内存数据库Redis   
1、快速了解Redis  

2、Redis的安装部署  

3、Redis基础命令  

4、Redis多数据库特性  

5、Redis常用数据类型之String  

6、Redis常用数据类型之Hash  

7、Redis常用数据类型之List  

8、Redis常用数据类型之Set  

9、Redis常用数据类型之Sorted Set  

10、案例：存储高一班的学员信息  

11、Java代码操作Redis之单连接  

12、Java代码操作Redis之连接池  

13、提取RedisUtils工具类  

14、Redis高级特性之expire  

15、Redis高级特性之pipeline  

16、Redis高级特性之info  

17、Redis持久化之RDB  

18、Redis持久化之AOF  

19、Redis的安全策略  

20、Redis监控命令-monitor  

21、Redis架构演进过程  

  
### 第16周   Flink快速上手篇   
1、快速了解Flink  

2、Flink Streaming程序开发  

3、Flink Batch程序开发  

4、Flink Standalone集群安装部署  

5、Flink ON YARN的第一种方式  

6、Flink ON YARN的第二种方式  

7、向集群中提交Flink任务  

8、Flink核心API介绍  

9、DataStream API之DataSource  

10、DataStream API之Transformation  

11、DataStream API之分区规则介绍  

12、DataStream API之分区规则的使用  

13、DataStream API之DataSink  

14、DataSet API之DataSource  

15、DataSet API之Transformation  

16、DataSet API之DataSink  

17、Table API 和 SQL介绍  

18、创建TableEnvironment对象  

19、TableAPI和SQL的使用  

20、使用DataStream创建表  

21、使用DataSet创建表  

22、将表转换成DataStream  

22、将表转换成DataSet  

  
### 第17周   Flink高级进阶之路   
1、Window的概念和类型  

2、TimeWindow的使用  

3、CountWindow的使用  

4、自定义Window的使用  

5、Window中的增量聚合和全量聚合  

6、Flink中的Time  

7、Watermark的分析  

8、开发Watermark代码  

9、通过数据跟踪观察Watermark  

10、Watermark+EventTime处理乱序数据  

11、延迟数据的三种处理方式  

12、在多并行度下的Watermark应用  

13、Watermark案例总结  

14、并行度介绍及四种设置方式  

15、并行度案例分析  

16、KafkaConsumer的使用  

17、KafkaConsumer消费策略设置  

18、KafkaConsumer的容错  

19、KafkaProducer的使用  

20、KafkaProducer的容错  

21、SparkStreaming的WordCount程序开发  

22、SparkStreaming整合Kafka  

  
## 阶段五：综合项目：三度关系推荐系统+数据中台  
### 第18周   直播平台三度关系推荐V1.0   
1、项目介绍  

2、项目需求分析  

3、技术选型  

4、整体架构设计  

5、Neo4j快速上手使用  

6、数据采集架构详细分析  

7、数据来源分析  

8、模拟产生数据  

9、数据采集聚合  

10、数据分发  

11、数据落盘  

12、数据计算核心指标详细分析与实现  

13、三度关系推荐页面数据接入  

14、三度关系推荐流程演示  

15、项目代码双语支持  

16、项目总结  

  
### 第19周   直播平台三度关系推荐V2.0   
1、现有V1.0技术架构分析  

2、V2.0技术架构设计  

3、数据计算核心指标详细分析  

4、历史粉丝关注数据初始化  

5、实时维护粉丝关注数据  

6、每天定时更新主播等级  

7、每天定时更新用户活跃时间  

8、每周一计算最近一月主播视频评级  

9、每周一计算最近一月主播视频评级  

10、三度关系列表数据导出到Redis  

11、数据接口定义与开发  

12、项目代码双语支持  

13、项目总结  

  
### 第20周   数据中台大屏   
1、什么是中台  

2、中台化主要解决的问题  

3、中台的延伸  

4、什么是数据中台  

5、数据中台演进的四个阶段  

6、数据中台需要具备三大能力  

7、企业级数据中台架构分析  

9、目前大数据领域实时计算的现状  

10、数据中台之数据加工总线介绍  

11、数据加工总线架构图分析  

12、开发数据加工总线计算引擎(基于SparkSQL)  

13、开发数据加工总线计算引擎(基于FlinkSQL)  

14、掌握如何在流式SQL中调用HTTP接口  

15、支持流式SQL中的自定义函数返回多列字段  

  
