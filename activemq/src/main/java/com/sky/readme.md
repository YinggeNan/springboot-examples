#### springboot应用入口
入口类main方法必须有SpringApplication.run(${入口类名称}.class, args);才能真正启动springboot应用，而且如果没有启动
springboot应用，一个简单的java类的main方法打出的log和sprinboot的log区别很大，首先没有springboot的logo，而且springboot的log都是
日志框架打印的，有时间戳，而普通java main方法运行没有这些东西。

#### springboot-activemq的starter默认会启动嵌入式的内存的activemq
如果要让项目使用外部的qctivemq，比如你想看activemq的管理界面之类的，并在界面上操作的话，你就需要使用外部activeqm
在application.properties里加如下配置
```
spring.activemq.broker-url=tcp://localhost:61616
```
#### @EnableJMS放到springboot入口类或configuration类上
作用是搜索被@JMSListener注解的方法，使其成为监听器

#### @JmsListener注解一个方法，让该方法监听一个目标topic或queue
参考:https://java2blog.com/spring-boot-activemq-example/

#### @CommandLineRunner注解bean的自定义run方法将在springboot入口类的main方法之前执行
用于初始化、加载一些数据，
多个被@CommandLineRunner注解的bean，可以用@Order来指定启动顺序,@Order指定的value值越小，优先级越高，越先执行run方法
参考:https://blog.csdn.net/ruben95001/article/details/78340700