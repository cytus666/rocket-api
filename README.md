# dataway2

### 摘要
1. 用于快速开发API接口。不再定义`Controller`,`Service`,`Dao`,`Mybatis`,`xml`,`Entity`,`VO`等对象.
2. 可视化界面，将入参自动封装到可执行的脚本上，支持所有关系性数据库SQL执行语句，非关系型`MONGODB`查询语句.
3. 完全基于springboot2.x,无侵入性，新老项目都能快速集成
4. 无需编写一行代码即可完成大部分的需求开发，使用难度级别（测试 or 运维）也可参与开发
5. 动态编译，无需重启，即时生效

### 快速开始
#####1. 添加依赖

```$xml
<dependency>
    <groupId>com.github.alenfive</groupId>
    <artifactId>dataway2-boot-starter</artifactId>
    <version>0.0.1-SNAPSHOT</version>
</dependency>
```

版本查看: https://github.com/alenfive/dataway2/releases  

#####2. 配置数据源,继承`com.github.alenfive.dataway2.datasource.DataSourceManager` 注入数据源

```java
@Component
public class DefaultDataSourceManager extends DataSourceManager {

    @Autowired
    private JdbcTemplate jdbcTemplate;

    @PostConstruct
    public void init() {

        Map<String,DataSourceDialect> dialects = new HashMap<>();
        //通过MysqlDataSource的第二个参数为`true`来表示生成的API信息所存储的库，有且仅有一个为true
        dialects.put("mysql",new MysqlDataSource(jdbcTemplate,true));
        super.setDialectMap(dialects);
    }
}
```

#####3. 关系型数据库建表，非关系型不用
最新建表脚本查看: https://github.com/alenfive/dataway2/tree/master/src/main/resources/script

>启动项目，访问地址: http://localhost:8080/api-ui

>文档地址1: https://github.com/alenfive/dataway2/wiki 

>文档地址2: https://gitee.com/mihuajun/dataway2/wikis/Home
  
