# AdvancedWebLab3
#### Spring Boot+Mybatis配置
##### 1. 下载并安装Maven
+ 下载apache-maven http://maven.apache.org/download.cgi ，解压到某个特定的目录（如apache-maven），将此目录下的子目录bin配置到系统环境变量Path中。
+ 修改apache-maven/conf下的文件settings.xml已使用阿里镜像加速项目的创建，内容参考 https://blog.csdn.net/freyaalisa/article/details/78648975
##### 2. 使用intellj创建Spring Boot+Mybatis项目
+ 参考 https://blog.csdn.net/weixin_42685022/article/details/82215893
+ 注意需要修改Group和Artifact

##### 3. 将Spring Boot与Mybatis联系起来
+ 将src/main/resources目录下的文件application.properties删除，在此目录下新建文件application.yml
+ 配置内容为
``` xml
server:
  port: 8080

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/adweb-lab3?serverTimezone=GMT%2B8
    username: root
    password: good2739966538
    driver-class-name: com.mysql.cj.jdbc.Driver

mybatis:
  // 实体类所在的包
  type-aliases-package: com.fudan.entity
  mapper-locations: classpath*:mapper/*.xml
```
##### 4. 安装并使用Mybatis Generator插件
+ 参考 https://blog.csdn.net/weixin_42685022/article/details/82215893
+ 配置文件generatorConfig.xml中targetProject属性值的设置请参考src/main/resources/generator/generatorConfig.xml

##### 5. 测试Spring Boot+Mybatis
+ 数据库中数据的配置参考lab3 Part2:Mybatis
+ 示例参考 https://blog.csdn.net/weixin_42685022/article/details/82215893
+ attentions
	+ Service需要使用注解@Autowired注入UserMapper
	+ Controller需要使用注解@Autowired注入UserService
