# 开发环境

* IDEA
* 构建工具：Maven
* MySQL
* MyBatis

# 创建 Maven 工程

1、将打包方式设置为 jar 的打包方式：

```xml
<packaging>jar</packaging>
```

2、引入依赖

[<font style="color:#003884;">pom.xml</font>](https://github.com/hzhiping/learn-code/blob/main/mybatis01/pom.xml)

# 创建 MyBatis 的核心配置文件
习惯上命名为 mybatis-config.xml，这个文件名仅仅只是建议，并非强制要求。将来整合 Spring 之后，这个配置文件可以省略，所以大家操作时可以直接复制、粘贴。

核心配置文件主要用于配置连接数据库的环境以及 MyBatis 的全局配置信息，核心配置文件存放的位置是 src/main/resources 目录下。

[<font style="color:#003884;">mybatis-config.xml</font>](https://github.com/hzhiping/learn-code/blob/main/mybatis01/src/main/resources/mybatis-config.xml)

# 创建 Mapper 接口

MyBatis 中的 Mapper 接口相当于以前的 DAO。但是区别在于，Mapper 仅仅是接口，我们不需要提供实现类。

[<font style="color:#003884;">UserMapper.java</font>](https://github.com/hzhiping/learn-code/blob/main/mybatis01/src/main/java/com/hzhiping/mapper/UserMapper.java)

# 创建 MyBatis 的映射文件

## 相关概念

ORM【Object Relationship Mapping】对象关系映射：

* 对象：Java 的实体类对象
* 关系：关系型数据库
* 映射：二者之间的对应关系

| Java 概念 | 数据库概念 |
| --- | --- |
| 类 | 表 |
| 属性 | 字段【列】 |
| 对象 | 记录【行】 |

## 映射文件的命名规则

* 表所对应的实体类的类名 + Mapper.xml，例如：表 User，映射的实体类为 User，所对应的映射文件为 UserMapper.xml
* 因此一个映射文件对应一个实体类，对应一张表的操作
* MyBatis 映射文件用于编写 SQL，访问以及操作表中的数据
* MyBatis 映射文件存放的位置是 src/main/resources/mappers 目录下

## 注意点

MyBatis 中可以面向接口操作数据，要保证两个一致：

* Mapper 接口的全类名和映射文件的命名空间【NameSpace】保持一致
* Mapper 接口中方法的方法名和映射文件中编写 SQL 的标签 id 属性保持一致

## 代码

[<font style="color:#003884;">UserMapper.xml</font>](https://github.com/hzhiping/learn-code/blob/main/mybatis01/src/main/resources/mappers/UserMapper.xml)

# 通过 JUnit 测试功能

SqlSession：代表 Java 程序和数据库之间的会话【HttpSession 是 Java 程序和浏览器之间的会话】。

SqlSessionFactory：是生产 SqlSession 的工厂。

工厂模式：如果创建某一个对象，使用的过程基本固定，那么我们就可以把创建这个对象的相关代码封装到一个“工厂类”中，以后都使用这个工厂类来“生产”我们需要的对象。

[<font style="color:#003884;">UserMapperTest.java</font>](https://github.com/hzhiping/learn-code/blob/main/mybatis01/src/test/java/com/hzhiping/test/UserMapperTest.java)

此时需要手动提交事务，如果要自动提交事务，则在获取 SqlSession 对象时，使用 SqlSession sqlSession = sqlSessionFactory.openSession(true)，传入一个 Boolean 类型的参数，值为 true，这样就可以自动提交。

# 加入 log4j 日志功能

1、加入依赖

```xml
<!-- log4j 日志-->
<dependency>
  <groupId>log4j</groupId>
  <artifactId>log4j</artifactId>
  <version>1.2.17</version>
</dependency>
```

2、加入 log4j 的配置文件

log4j 的配置文件名为 log4j.xml，存放的位置是 src/main/resources 目录下

日志的级别：FATAL【致命】> ERROR【错误】> WARN【警告】> INFO【信息】> DEBUG【调试】从左到右打印的内容越来越详细

[<font style="color:#003884;">log4j.xml</font>](https://github.com/hzhiping/learn-code/blob/main/mybatis01/src/main/resources/log4j.xml)