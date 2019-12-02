---
title: "Bean自动加载"
date: 2019-12-02T17:25:35+08:00
draft: false
tags: ["java", "spring"]
---
通常来讲，要想实现上面的场景，建议是借助@Configuration注解的配置类来管理你自己的bean，这样对于其他使用方而言，只需要加载到你的配置类，就可以注册你的所有bean了。

1. 包路径扫描使用姿势

    首先是在你的工程中定义一个配置类，如下

    ```java
    @Configuration
    @ComponentScan("com.git.hui.boot.autoconfig")
    public class SelfAutoConfig {
    }
    ```
    这个配置类功能比较简单，指明扫描的包路径，然后这个配置类如何给使用方使用呢？
    将配置放在指定的文件中即可，使用者会自动加载，从而避免的代码的侵入。

    在资源目录下新建目录 META-INF，在 META-INF 目录下新建文件 spring.factories，在文件中添加 

    ```ini
    org.springframework.boot.autoconfigure.EnableAutoConfiguration=com.git.hui.boot.autoconfig.SelfAutoConfig
    ```
    
    说明，如果需要换行时，可以如下

    ```ini
    org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
        com.git.hui.boot.autoconfig.SelfAutoConfig,`
        com.git.hui.boot.autoconfig.SelfAutoConfig2,`
    ```
    
    然后使用方就可以愉快的使用你的bean了

1. 定义Bean使用方式
    直接在Config配置中，定义Bean，可以说是更加常见的方式，特别是当你的bean不是那么多的时候，推荐使用这种方式，便于集中管理

    ```java
    @Slf4j
    public class AutoConfBean {
        private String name;

        public AutoConfBean(String name) {
            this.name = name;
            log.info("AutoConfBean load time: {}", System.currentTimeMillis());
        }

        public String getName() {
            return name;
        }
    }
    ```
    对应的配置类
    ```java
    @Configuration
    @ComponentScan("com.git.hui.boot.autoconfig")
    public class SelfAutoConfig {

        @Bean
        public AutoConfBean autoConfBean() {
            return new AutoConfBean("auto load + " + System.currentTimeMillis());
        }
    }
    ```