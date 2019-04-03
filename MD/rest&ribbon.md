# 服务消费者（rest+ribbon）
+ 微服务架构中，业务会被拆分成独立的服务，服务与服务的通讯是基于http restful
+ Spring cloud有两种服务调用方式，一种是ribbon+restTemplate，另一种是feign
+ ribbon是一个负载均衡客户端，feign默认集成了ribbon
+ idea通过Edit Configuration=》默认的Single instance only(单实例)的钩去掉，可实现通个项目启多个实例
### 建一个服务消费者
+ 新建一个spring-boot工程
+ 和新建service、client类似
+ pom依赖ribbon
+ 启动application类加注解@EnableDiscoveryClient，像服务中心注册
+ @LoadBalanced注解表明这个restRemplate开启负载均衡的功能
### 此时的架构
![加入负载后的架构](http://upload-images.jianshu.io/upload_images/2279594-9f10b702188a129d.png)
+ 一个注册中心
+ service-hi跑了两个实例，分别向服务注册中心注册
+ service-ribbon向服务注册中心注册
+ service-ribbon通过restTemplate调用service-hi的hi接口，用ribbon进行了负载均衡，会轮流的调用service-hi



