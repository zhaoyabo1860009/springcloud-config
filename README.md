# springcloud-config
#创建一个本地测试使用的配置中心

git本地仓库操作：
 git clone https://github.com/xxx/springcloud-config.git
 git add .
 执行git commit -m "First commit"命令，提交到本地的版本控制库里，引号里面是你对本次提交的说明信息。
 最后，执行” git push origin master“命令将本地仓库提交到远程的GitHub中，这里会用到注册的用户名和密码。输入密码的时候默认是没有任何提示符。
 
 构建springcloud-config服务
1、pom.xml
   <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-config-server</artifactId>
            <version>2.0.1.RELEASE</version>
        </dependency>
2、application.yml	
  spring:
  application:
    name: com.cncbox.springcloud.config
  cloud:
    config:
      server:
        git:
          uri: https://github.com/xxxxxx/springcloud-config.git
          username: xxxxx
          password: xxxxx
          ####搜索目录
          search-paths:
            - springcloud-config
      ########读取分支
      label: master
3、启动类
@EnableConfigServer
4、

访问在本地模拟，在本地hosts文件中配置一个域名进行模拟
例如：springcloud-config.com
http://springcloud-config.com:10007/master/config-prod.yml
