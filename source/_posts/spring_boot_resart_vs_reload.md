---
title: spring boot resart vs reload
categories:
- spring
- boot
date: 2017-02-09 17:30
---
### 简介：
1. restart
是有两个classloader，一个加载依赖中的类，另一个加载编写的类，当检测到编写的类发生变化时会创建新的classloader来加载编写的类,原classloader将结束，但当工程变大的时候每次restart的速度变慢。
2. reload
是会在类文件发生变化时更新类文件，所以只有当类和方法签名不变的情况下才能正常工作，也就是说当添加类或者方法，改变方法参数结构是都不能工作。但是启动速度很快。

### 启动方式
1. restart:任意一种启动方式都可以。
2. reload:需要使用maven 插件，命令：mvn spring-boot:run,或者点击idea maven中的插件spring-boot:run运行。

### 使用场景对比
* restart适用于前期开发阶段，这个阶段主要是添加类和方法且工程较小。
* reload适用于后期开发阶段，这个阶段主要是修改具体实现，且工程较大。

### 配置
1. restart 配置
{% codeblock lang:xml %}
  <build>
      <plugins>
          <plugin>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-maven-plugin</artifactId>
              <version>1.2.5.RELEASE</version>
              <dependencies>
                  <dependency>
                      <groupId>org.springframework</groupId>
                      <artifactId>springloaded</artifactId>
                      <version>1.2.4.RELEASE</version>
                  </dependency>
              </dependencies>
          </plugin>
      </plugins>
  </build>
{% endcodeblock %}
2. reload配置
{% codeblock lang:xml %}
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>
{% endcodeblock %}
