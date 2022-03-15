# SSMM整合及其层级中的包

## util
util一般来说，就是一个明确的输入和一个明确的输出结果。工具类存放封装好的工具，如改写的输入输出，加解密等。

## bean
存放**最简单的Java对象**，负责逻辑的处理，数据的操作等。如加密一段信息，对信息做签名。

## dao
主要是做数据库持久的操作，增删改查等。负责与数据库进行联络的一些任务都封装在此包。
**首先要设计dao层的接口（dao目录下），然后在resources目录下mapper包下实现该接口的SQL语句（XML文件）。**

## service
主要负责业务模块的应用逻辑设计。首先是**设计接口然后实现该接口，一个Service只对应一个Dao**。
Service会做一些额外的检查，如货物是否损坏，入库单是否完整等。

## controller
负责具体的业务模块**流程的控制**，调用service层的接口来控制业务流程。

## 总结
dao是一种比较底层，比较基础的操作，对于数据库的操作，具体到对于某个表的增删改查，
也就是说某个dao一定是和数据库的某一张表一一对应的，其中封装了增删改查基本操作，
建议dao只做原子操作，增删改查。

service层被称为服务，就是对一个或多个dao(增删改查等基本操作)进行再次封装，封装成一个服务，
所以这里也就不会是一个原子操作了，需要事物控制。

controller是业务层，管理用户的操作，用户界面传过的请求，调用对应的service，完成用户请求的处理。