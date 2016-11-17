## Maven
### Maven安装  
安装前保证环境变量能使用jdk，在maven官网下载相应的二进制包，解压并配置好环境变量即可。  


### mvn  
#### 命令  
mvn pom.xml文件配置详解   
http://maven.apache.org/ref/2.0.8/maven-model/maven.html   

mvn -version/-v 显示版本信息   
mvn archetype:generate   创建mvn项目   
mvn archetype:create -DgroupId=com.oreilly -DartifactId=my-app   创建mvn项目   

mvn package    生成target目录，编译、测试代码，生成测试报告，生成jar/war文件   
mvn jetty:run    运行项目于jetty上,   
mvn compile      编译   
mvn test      编译并测试   
mvn clean      清空生成的文件   
mvn site      生成项目相关信息的网站   
mvn -Dwtpversion=1.0 eclipse:eclipse   生成Wtp插件的Web项目   
mvn -Dwtpversion=1.0 eclipse:clean   清除Eclipse项目的配置信息(Web项目)   
mvn eclipse:eclipse     将项目转化为Eclipse项目  

在应用程序用使用多个存储库  
```
    <repositories>    
    <repository>      
       <id>Ibiblio</id>      
       <name>Ibiblio</name>      
       <url>http://www.ibiblio.org/maven/</url>    
    </repository>    
    <repository>      
       <id>PlanetMirror</id>      
       <name>Planet Mirror</name>      
       <url>http://public.planetmirror.com/pub/maven/</url>    
    </repository> 
    </repositories> 
```   

mvn deploy:deploy-file -DgroupId=com -DartifactId=client -Dversion=0.1.0 -Dpackaging=jar -Dfile=d:\client-0.1.0.jar -DrepositoryId=maven-repository-inner -Durl=ftp://xxxxxxx/opt/maven/repository/ 

mvn -e    显示详细错误 信息.   
mvn validate   验证工程是否正确，所有需要的资源是否可用。   
mvn test-compile 编译项目测试代码  
mvn integration-test 在集成测试可以运行的环境中处理和发布包。   
mvn verify   运行任何检查，验证包是否有效且达到质量标准。   
mvn generate-sources 产生应用需要的任何额外的源代码，如xdoclet  

### maven仓库  
#### 包查询  
1. [https://mvnrepository.com/](https://mvnrepository.com/)  