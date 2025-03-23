# MyBatis 的核心配置文件

核心配置文件中的标签必须按照固定的顺序【有的标签可以不写，但顺序一定不能乱】：

* properties
* settings
* typeAliases
* typeHandlers
* objectFactory
* objectWrapperFactory
* reflectorFactory
* plugins
* environments
* databaseIdProvider
* mappers

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
"http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
  <!-- 引入 properties 文件，此时就可以 ${属性名} 的方式访问属性值 -->
  <properties resource="jdbc.properties"></properties>
  <settings>
    <!-- 将表中字段的下划线自动转换为驼峰 -->
    <setting name="mapUnderscoreToCamelCase" value="true"/>
    <!-- 开启延迟加载 -->
    <setting name="lazyLoadingEnabled" value="true"/>
  </settings>
  <typeAliases>
    <!--
      typeAlias：设置某个具体的类型的别名
      属性：
        type：需要设置别名的类型的全类名
        alias：设置此类型的别名，且别名不区分大小写。若不设置此属性，该类型拥有默认的别名，即类名
    -->
    <!-- <typeAlias type="com.hzhiping.bean.User"></typeAlias> -->
    <!-- <typeAlias type="com.hzhiping.bean.User" alias="user"></typeAlias> -->
    <!-- 以包为单位，设置改包下所有的类型都拥有默认的别名，即类名且不区分大小写 -->
    <package name="com.hzhiping.bean"/>
  </typeAliases>
  <!--
  environments：设置连接数据库的环境
  属性：
  id：表示链接数据库的环境的唯一标识，不能重复
  -->
  <environments default="development">
    <environment id="development">
      <!--
      transactionManager：设置事务管理方式
      属性：
      type="JDBC|MANAGED"
      JDBC：
      MANAGED：
      -->
      <transactionManager type="JDBC"/>
      <!--
      dataSource：配置数据源
      属性：
      type：
      type="POOLED|UNPOOLED|JNDI"
      POOLED：使用数据库连接池，即会将创建的连接进行缓存，下次使用可以从缓存中直接获取，不需要重新创建
      UNPOOLED：不使用数据库连接池，即每次使用链接都需要重新创建
      JNDI：使用上下文中的数据源
      -->
      <dataSource type="POOLED">
        <!-- 设置驱动类的全类名 -->
        <property name="driver" value="${jdbc.driver}"/>
        <!-- 设置连接数据库的连接地址 -->
        <property name="url" value="${jdbc.url}"/>
        <!-- 设置连接数据库的用户名 -->
        <property name="username" value="${jdbc.username}"/>
        <!-- 设置连接数据库的密码 -->
        <property name="password" value="${jdbc.password}"/>
      </dataSource>
    </environment>
  </environments>
  <!-- 引入映射文件 -->
  <mappers>
    <mapper resource="mappers/UserMapper.xml"/>
    <!--
      以包为单位，将包下面的所有的映射文件引入核心配置文件，注意：
      1、此方式必须保证 mapper 接口和 mapper 映射文件必须在相同的包下
      2、mapper 接口要和 mapper 映射文件的名字一致
    -->
    <!-- <package name="com.hzhiping.mapper"/> -->
  </mappers>
</configuration>
```