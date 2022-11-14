
## MongoDB

**MongoDB简介**

MongoDB是一种基于**分布式文件存储**的NoSQL数据库。由C++语言编写。旨在为WEB英语提供可扩展的高性能数据存储方案。<br/>
MongoDB是一个介于关系型数据库和非关系型数据之间的产品，是非关系型数据库当中功能最丰富，最像关系型数据的。

**MongoDB特点**

- 模式自由：可以把不同结构的文档存储到同一个数据库中。
- 面向集合的存储：适合存储JSON风格文件的形式。
- 完整的索引支持：对任何属性可索引。
- 自动分片：支持云级别的伸缩，自动分片功能支持水平的数据库集群，可动态添加额外的机器。
- 高效的传统存储方式：支持二进制数据及大对象（图片等）。
- 丰富的查询功能：支持丰富的查询方式，支持使用JSON形式，可以轻易的查询文档中嵌套（内嵌）的对象或数据。
- 复制性高可用性：支持服务器之间的数据复制，支持主从模式及服务器之间的相互复制，复制的主要目的是提供冗余及自动故障转移。
- 快速的更新操作：查询优化器会分析查询表达式，并生成一个高效的查询计划。

根据DB-Engine-Ranking的排名统计截止到2021年-9月Mongodb排名第五，见截图：

![avatar](../../../../media/pictures/Mongdb-Rank.png)

## NOSQL

**什么是NOSQL**

NOSQL(NOSQL=Not Only SQL),即不仅仅是SQL，是指非关系型数据库，是对于不同传统关系型数据库的统称。

**关系型数据库的瓶颈**

- 关系型数据库具有不错的稳定性，高性能，使用简答，功能强大，历史悠久，并且有很多成功的案例。
- 在互联网领域，Mysql成为了绝对的王者，毫不夸张的说，MySQL为互联网的发展做出了卓越的贡献。
- 随着时代的发展电商的发展引领了WEB时代的潮流，导致流量一下增大到无法想象的地方。

**缓存+MySQL数据库**

- 随着访问量的增加，使用MySQL的网站基本上都出现了性能的问题，为了追求极值的性能，采用了缓存技术来环节流量高峰数据库的压力。

**MySQL主从读写分离**

由于数据写入的压力增加，（缓存只能解决读取的压力）。未做读写分离的数据库会频繁的引发告警例如cpu、内存或IO异常。所有后来技术架构演进到
读写分离技术，Mysql的master-slave可实现主从复制功能，读写分离中间件可使用MySQL-Proxy、MyCat、sharding-jdbc等等，这里我们不做详细介绍。

**NOSQL优势**

****易扩展****

NOSQL数据库去掉了数据库关联关系的特性，数据之间无关联关系，这就就非常容易扩展字段（新增字段）

****大数据高性能****

在大数据量的情况下，NOSQL数据库都具有非常高的读写性能，这取决于它无关联关系特性。


****灵活的数据模型****

NOSQL无需提前为存储的字段建立字段，可随时存储自定义的字段内容。而关系型数据库在新增或删除字段是一件非常麻烦的事情。如果数据量非常大的情况下，简直就是噩梦。
（PS:笔者曾经给2000w的mysql表新增了一个字段，我记得当时耗时2小时。）

****高性能****

NOSQL在不影响性能的情况下，就可以实现高可用的架构。

****NOSQl适用场景****
1. 简单的数据模型
2. 对数据库性能要求高
3. 不需要高度的数据一致性
4. 容易扩展字段

## MongoDB适用场景

MongoDB是一个可扩展的高性能、开源、面向文档的数据。

**适用场景**

- 网站数据：实时的插入、删除、更新、查询，以及数据的复制性和高度伸缩性
- 缓存：由于高性能，适合作为系统的缓存层，在系统异常重启后缓存可以缓解数据库的压力
- 廉价的存储成本：使用传统型数据库存储数据的成本会比较高
- 高伸缩的场景：非常适合集群模式下组成的数据库，可随时新增节点
- 用于对象及JSON的数据存储：MongDB的BSON数据格式存储非常适合文档格式的存储及查询

**不适用场景**

- 高度的事务系统：例如银行系统、会计系统，对事务要求比较高
- 传统的商业智能系统：会产生高度的sql查询功能，对于这种业务数仓数据库会比较适合

**应用案例**

- 京东：使用MongoDB存储商品信息
- 赶集网：使用MongoDB记录pv的浏览计数
- 奇虎360：使用MongoDB支撑HULK平台每天200亿次的查询
- 百度云：使用MongoDB管理百度云盘中500亿关于文件源信息的记录
- 纽约时报：使用MongoDB存储存储门户网站的新闻信息

## 环境安装

**Window-MongoDB**

MongoDB 提供了可用于 32 位和 64 位系统的预编译二进制包，你可以从MongoDB官网下载安装，MongoDB 预编译二进制包下载地址：<https://www.mongodb.com/try/download/community>
>注意：在 MongoDB 2.2 版本后已经不再支持 Windows XP 系统。最新版本也已经没有了 32 位系统的安装文件。

<img src="./media/pictures/mongodb/mongodb-download.png" />

下载 .msi 文件，下载后双击该文件，按操作提示安装即可。安装过程中，你可以通过点击 "Custom(自定义)" 按钮来设置你的安装目录。
<img src="./media/pictures/mongodb/accpet.png" />

选择自定义模式

<img src="./media/pictures/mongodb/custom.png" />

选择文件路径

<img src="./media/pictures/mongodb/folder-name.png" />

选择数据盘、日志目录

<img src="./media/pictures/mongodb/data-log-directory.png" />

下一步安装 "install mongoDB compass" 不勾选（当然你也可以选择安装它，可能需要更久的安装时间），MongoDB Compass 是一个图形界面管理工具，

<img src="./media/pictures/mongodb/compass.png" />

至此整个安装的过程基本就完成了

<img src="./media/pictures/mongodb/status.png" /><br/>
<img src="./media/pictures/mongodb/finish.png" />

然后再刚才的安装目录（笔者的安装目录是D:\Program Files\MongoDB\Server\5.0\bin），找到mongo.exe双击打开，出现如下界面

<img src="./media/pictures/mongodb/mongo-exe.png" />

这个界面显示了mongodb的基本信息，然后再输入db.statu命名出现如下界面

<img src="./media/pictures/mongodb/db-status.png" />

下面我介绍一下各个参数的含义
```
"db" : "test" ,表示当前是针对"test"这个数据库的描述。想要查看其他数据库，可以先运行$ use datbasename
"collections" : 3,表示当前数据库有多少个collections.可以通过运行show collections查看当前数据库具体有哪些collection.
"objects" : 267,表示当前数据库所有collection总共有多少行数据。显示的数据是一个估计值，并不是非常精确。
"avgObjSize" : 623.2322097378277,表示每行数据是大小，也是估计值，单位是bytes
"dataSize" : 16640,表示当前数据库所有数据的总大小，不是指占有磁盘大小。单位是bytes
"storageSize" : 110592,表示当前数据库占有磁盘大小，单位是bytes,因为mongodb有预分配空间机制，为了防止当有大量数据插入时对磁盘的压力,因此会事先多分配磁盘空间。
"numExtents" : 0,没有什么真实意义
"indexes" : 2 ,表示system.indexes表数据行数。
"indexSize" : 53248,表示索引占有磁盘大小。单位是bytes
```





**Linux-MongoDB**


## 概念解释

**什么是MongoDB**

- MongoDB 是由C++语言编写的，是一个基于分布式文件存储的开源数据库系统。
- 在高负载的情况下，添加更多的节点，可以保证服务器性能。
- MongoDB 旨在为WEB应用提供可扩展的高性能数据存储解决方案。
- MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。
![avatar](../../../../media/pictures/mongodb-document.png)

**数据库**

数据库是一个集合的物理服务器，一个MongoDB服务器通常包含多个数据库

**集合**

集合存储在数据库中，没有固定的结构，可以插入不通类型的数据库，通常插入的数据是具有一定关联性的。例如插入如下数据到MongoDB中。（当第一个集合插入时集合就创建了）<br/>
 ```
     {"site":"www.baidu.com"}
     {"site":"www.google.com","name":"谷歌"}
     {"site":"www.oschina.cn","name":"开源中国","num":5}
 ```

**文档**

就是一组键值对 key-value

**NOSQlvsMongoDB**

| **SQL术语/概念** | **MongoDB术语/概念** | **解释/说明**                                        |
| ---------------- | -------------------- | ---------------------------------------------------- |
| database         | database             | 数据库                                               |
| table            | collection           | 数据库表/集合                                        |
| row              | document             | 数据记录行/文档                                      |
| column           | field                | 数据属性/字段(域)                                    |
| index            | index                | 索引                                                 |
| table joins      | Embedded Documents   | 表连接,MongoDB3.2提供了Join操作                      |
| primary key      | primary key          | 主键,MongoDB默认自动将_id字段设置为主键,可以手动设置 |

通过下图实例，我们也可以更直观的的了解Mongo中的一些概念：
![avatar](../../../../media/pictures/mysql-mongodb.png)

**ObjectId**

ObjectId类似唯一主键，可以很快的生成和排序，包含12bytes，含义是：

<img src="./media/pictures/mongodb/objectid.jpeg" />

- 前4个字节表示创建unix时间戳，格林威治的UTC时间，比北京时间晚8小时
- 接下来的3个字节是机器标识码
- 接下来的2个字节是进程ip组成的pid
- 最后三个字节是随机数



## 高级操作











