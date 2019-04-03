# 服务消费者（Feign）

## 简介
+ 采用了基于接口的注解
+ Feign整合了ribbon,具有负载均衡能力
+ 整合了Hystrix,具有熔断能力
## 创建一个Feign
+ 创建过程跟之前类似
+ application启动类加上@EnableFeignClients注解开启Feign的功能
+ 定义feign接口，通过FeignClient（“服务名”）指定调用哪个服务
```java
@FeignClient(value = "service-hi")
public interface SchedualServiceHi {
    @RequestMapping(value = "/hi",method = RequestMethod.GET)
    String sayHiFromClientOne(@RequestParam(value = "name") String name);
}
```
+ controller层，对外暴露一个"/hi"的API接口，通过定义的接口，消费服务
