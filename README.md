# SpringCloud demo
+ 基于Eureka组件的服务注册发现

## 过程
### 主Maven工程搭建
+ 首先创建一个主Maven工程，在其pom文件引入依赖，spring Boot版本为2.0.3.RELEASE
+ Spring Cloud版本为Finchley.RELEASE。这个pom文件作为父pom文件，起到依赖版本控制的作用，其他module工程继承该pom
### 创建2个model工程
+ 一个model工程作为服务注册中心，即Eureka Server,另一个作为Eureka Client
+ Eureka作为服务注册与发现的组件
+ eureka是一个高可用的组件，它没有后端缓存，每一个实例注册之后需要向注册中心发送心跳（因此可以在内存中完成），在默认情况下erureka server也是一个eureka client ,必须要指定一个 server
+ 市面上nacos用的多一点
+ ***Eureka Server(服务注册中心)***
  + 右键工程->创建model-> 选择spring initialir
  + dependencies选择cloud discovery->eureka server
  + 创建完后的工程，其pom.xml继承了父pom文件，并引入spring-cloud-starter-netflix-eureka-server的依赖
  + 启动一个服务注册中心，在启动application类上加上注解@EnableEurekaServer
  + eureka server的配置文件appication.yml
  + eureka.client.registerWithEureka：false和fetchRegistry：false来表明自己是一个eureka server,否则会尝试将自己作为客户端来尝试注册它自己，报Cannot execute request on any known server
+ ***Eureka Client(服务提供者)***
  + 创建过程和server类似
  + 注解使用EnableEurekaClient，表名自己是服务提供者
  