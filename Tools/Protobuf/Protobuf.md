## Protobuf

### 常见问题  
#### eclipse安装protobuf-dt插件问题  
在eclipse中轻松的使用protobuf，首先需要安装一个插件叫protobuf-dt,介绍及安装说明：[https://code.google.com/p/protobuf-dt/](https://code.google.com/p/protobuf-dt/)  
安装protobuf-dt时，  
1. 安装顺序不能乱，先安装xtext,再安装protobuf-dt  
2. xtext插件只安装xtext ui组件，其他的不要安装，不然后面安装protobuf-dt的时候会有依赖冲突  
3. protobuf-dt和xtext插件的版本有关系，protobuf-dt的最新版本依赖的是xtext2.4.2版本，因此安装时记得选对版本，官方安装说明里那个已经过时了是很早以前的安装说明  

安装好后，就可以在eclipse里非常方便的编写自己的.proto文件了。file-new中也会有新建.proto文件。  
新建一个maven项目，添加依赖  
```
<dependency>
  <groupId>com.google.protobuf</groupId>
  <artifactId>protobuf-java</artifactId>
  <version>2.5.0</version>
</dependency>
```

在项目的properties中编辑protobuf插件的选项可以进行相应设置  
1. main选项中设置编译.proto文件的protoc.exe，这样每次编辑完.proto文件后保存的时候会自动重新生成新的java文件。  
2. 由于是maven项目，可以把生成代码的路径改为src/main/java(默认是src-gen)。  


### 参考链接  
1. [gRPC 官方文档中文版](http://doc.oschina.net/grpc?t=60138)  
2. [grpc python documents](http://www.grpc.io/grpc/python/index.html#)
3. [Protobuf语言指南](http://www.cnblogs.com/dkblog/archive/2012/03/27/2419010.html)   