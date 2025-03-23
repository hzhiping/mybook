# MyBatis 的增删改查


[UserMapper.xml](https://github.com/hzhiping/learn-code/blob/main/mybatis01/src/main/resources/mappers/UserMapper.xml)

## 添加

```xml
<!-- int insertUser(); -->
<insert id="insertUser">
  insert into user
  values (null, '张三', '123', 23, '女')
</insert>
```

## 删除

```xml
<delete id="deleteUser">
    delete
    from user
    where id = 5
</delete>
```

## 修改

```xml
<update id="updateUser">
    update user
    set username = "张三"
    where id = 6
</update>
```

## 查询一个实体类对象

```xml
<select id="getUserById" resultType="com.hzhiping.bean.User">
    select *
    from user
    where id = 6
</select>
```

# 查询集合

```xml
<select id="getUserList">
    select *
    from user
</select>
```

# 注意

* 查询的标签 select 必须设置属性 resultType 或 resultMap，用于设置实体类和数据库表的映射关系
    * resultType：自动映射，用于属性名和表中字段名一致的情况
    * resultMap：自定义映射，用于一对多或多对一或字段名和属性名不一致的情况
* 当查询的数据为多条时，不能使用实体类作为返回值，只能使用集合，否则会抛出异常 TooManyResultsException；但是若查询的数据只有一条，可以使用实体类或集合作为返回值