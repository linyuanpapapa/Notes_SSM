## Mybatis

1. 什么是框架？

   1. 它是我们软件开发中的一套解决方案，不同的框架解决的是不同的问题
   2. 使用框架的好处：框架封装了很多的细节，使开发者可以使用极简的方式实现功能，大大提高开发效率

2. 三层架构

   1. 表现层：是用于展示数据的
   2. 业务层：是处理业务需求的
   3. 持久层：是和数据库交互的

3. 持久层技术解决方案：

   1. JDBC技术：Connection、PreparedStatement和ResultSet
   2. Spring的JdbcTemplate：Spring中对jdbc的简单封装
   3. Apache的DBUtils：它和Spring的JdbcTemplate很像，也是对Jdbc的简单封装
   4. 以上都不是框架：jdbc是规范，Spring的JdbcTemplate和Apache的DBUtils都是工具类

4. mybatis的概述

   1. mybatis是一个用Java编写的持久层框架，它封装了jdbc操作的很多细节，使开发者只需要关注sql语句本身，而无需关注注册驱动，创建连接等繁杂过程，它使用了ORM思想实现了结果集的封装。
   2. ORM：Object Relational Mapping对象关系映射，把数据库表和实体类以及实体类的属性对应起来，让我们可以操作实体类就操作数据库表。（实体类中的属性和数据库表的字段名称保持一致）

5. mybatis的入门

   1. mybatis的环境搭建

      1. 创建Maven工程并导入坐标
      2. 创建实体类和dao的接口
      3. 创建Mybatis的主配置文件：SqlMapConfig.xml
      4. 创建映射配置文件：UserDao.xml

   2. 环境搭建的注意事项

      1. 创建UserDao.xml和UserDao.java时名称一样是为了和之前的知识保持一致，在Mybatis中它把持久层的操作接口名称和映射文件叫做：Mapper。所以UserDao和UserMapper是一样的。
      2. 在IDEA中创建目录的时候，它和包是不一样的，包在创建时：cn.yuan.dao是三级结构，目录在创建时：cn.yuan.dao是一级目录
      3. Mybatis的映射配置文件位置必须和Dao接口的包结构相同
      4. 映射配置文件的mapper标签namespace属性的取值必须是dao接口的全限定类名
      5. 映射配置文件的操作配置（select），id属性的取值必须是dao接口的方法名
      6. 当遵从了345点后，我们在开发中就无须再写dao的实现类

   3. mybatis的快速入门 

      1. 读取配置文件
      2. 创建SqlSessionFactory工厂
      3. 创建SqlSession
      4. 创建Dao接口的代理对象
      5. 执行dao中的方法
      6. 释放资源
      7. 注意事项：不要忘记在映射配置文件中告知mybatis要封装到哪个实体类中，配置的方式：指定实体类的全限定类名。

      - mybatis基于注解的入门：把UserDao.xml移除，在dao接口的方法上使用@select注解，并且指定SQL语句，同时需要在SqlMapConfig.xml的mapper配置时，使用class属性指定dao接口的全限定类名。
      - 注意，在实际开发中，要求简便，不管使用XML还是注解配置，Mybatis都支持写dao实现类
