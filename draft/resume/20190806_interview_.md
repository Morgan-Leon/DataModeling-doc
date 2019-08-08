# 20190806 interview 

### SQL 增删改查 权限设定 

```
insert  into EMP  ( EMPNO, ENAME, MGR, JOB, HIREDATE, SAL, COMM, DEPTNO) 
values (0629, 'LYN',7499,'TEST' ,sysdate,1600,200,30);
 
delete EMP where EMPNO = 629;

update EMP set HIREDATE = to_date('19910629','yyyymmdd') where empno=629;

select EMPNO, ENAME, MGR, JOB, HIREDATE, SAL, COMM, DEPTNO
  from EMP
 where SAL > 0
 group by EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO
 having COMM is not null
 order by SAL desc;

```

`` 	grant dba to user_name; ``

### NoSQL 增删改查
```
db.students.insert({"name":"ziksang"})


db.dropDatabase()
删除你所在的当前数据库！！这个一定要小心，不会给你任何提示，然后就删除了
db.students.drop()
删除数据库中students集合
db.students.remove({"age":20})
删除所有students集合中age:20的文档


单个修改
db.students.update({"name":"qqqqqq"},{$set:{"age":100}})
把学生集合中 name =qqqqq 的 age改成100，但只能修改最上面的一条
多个修改
db.students.update({},{$set:{"age":100}},{multi:true})
查询条件为所有，把所有人的年纪都改成100                   mult:true  这个表示多条件更改

db.students.find({"scroe.shuxue":{$gt:50}})
选择数学成绩大于50的
db.students.find({"scroe.shuxue":{$gte:80}})
选择数学成绩大于等于80的

db.students.find().sort({"scroe.shuxue":-1,"age":1})
排列，进入学生集合查询，进行 分数降序排，如果分数相同，则年龄升序排 -1表示降序 1表示升序
```
### KETTLE 机制
KETTLE是一个纯JAVA编写的ETL工具。
我们项目组的任务是将数据源中的数据抽取出来，经过转化，传给业务系统。数据源一般来自于港澳资讯和万德。由于业务系统，开发的时间有早有晚，各系统间使用的技术差异很大，对数据格式有不同的要求。所以需要经过KETTLE进行抽取和转化。比如转化为TXT格式、DBF格式或者直接导入目标数据库。（Oracle到MySQL）等。
我们设计了一个配置文件，配置文件也是数据库中的一张表。表中有数据抽取的SQL或SP。
然后在KETTLE中执行这个SQL，再将结果按照需求进行转换。再输出出来。

### 投研系统
管理研报的，经历了几次重大升级，有包括盈利数据预测、实施新会计准则以及切换邮件服务器。
盈利数据预测这块，模型、研报还有网页上，这里的数据来源不同。
新会计准则，需要升级估值模型，新增研发费用
切换邮件服务器，使用JMeter进行压力测试。

### Spring Boot 
使用MAVEN构建项目

### 并发
#### 线程安全
synchronized
#### 线程池
使用Executors类，生成线程池

### 维度建模

  ##### 维度模型和第三范式的区别
  ACID 原子性（atomicity，或稱不可分割性）、一致性（consistency）、隔离性（isolation，又称独立性）、持久性（durability）
  * 1NF  同一列不能有多值
  * 2NF  实体的属性完全依赖于主关键字
  * 3NF 无冗余数据（非主属性只存一次）
  
  因为更新、插入等操作在BI中很少使用，3NF结构在业务处理中非常有用，但对于BI查询来说过于复杂。在DW/BI的数据展现层中使用3NF建模会破坏直观、高性能的数据检索。

  ##### 事实表和维度表的区别
   事实表和维度表的关键在于理解什么是事实。 一个交易就是一个事实。比如在面包店,售货员用扫码枪扫了一下面包，又扫了一下你的支付宝，这就进行了一次交易。这是产生的数据应被放到事实表中。
  ##### 星型模型和CUBE的区别
   维度模型实现在关系型数据库中 称为star schemas(星型结构)

   维度模型实现在多维数据库结构中 称为 OLAP cube

### PYTHON 
生成Excel报表:  xlwt
自动化测试 selenium
爬虫 requests

### 设计模式

### 自我介绍

Hello, everyone. My name is Morgan. I graduated from Beijing Jiaotong University in 2016 .

I'm not very good at spoken English, but I can read and write.

I learn programming through English books. When I was in college, my C++ teacher was an American. The textbook he used is called Dragon Book because it had a dragon on its cover,  written in English.

I like reading English programming books because I think Chinese translations are too bad.
Later, I learned the data warehouse, which is also an English book ，《The Data Warehouse Toolkit, 3rd Edition》.