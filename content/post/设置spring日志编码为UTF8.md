---
title: "设置spring日志编码为UTF8"
date: 2019-12-04T10:31:25+08:00
draft: false
tags: ["spring", "java"]
---
在resources中新增logback-spring.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration scan="true">
    <!-- use Spring default values -->
    <include resource="org/springframework/boot/logging/logback/defaults.xml"/>

    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>${CONSOLE_LOG_PATTERN}</pattern>
            <charset>utf8</charset>
        </encoder>
    </appender>
    …
</configuration>
```
