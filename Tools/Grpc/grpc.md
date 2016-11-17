## GRPC
### eclipse + maven + protobuf + grpc  
环境要求：在eclipse上配置好maven、protobuf  
1. 在eclipse中新建maven项目  
2. 在自动生成的pom.xml文件中加入以下内容用以下载grpc的jar包  
```
<dependency>
  <groupId>io.grpc</groupId>
  <artifactId>grpc-netty</artifactId>
  <version>1.0.1</version>
</dependency>
<dependency>
  <groupId>io.grpc</groupId>
  <artifactId>grpc-protobuf</artifactId>
  <version>1.0.1</version>
</dependency>
<dependency>
  <groupId>io.grpc</groupId>
  <artifactId>grpc-stub</artifactId>
  <version>1.0.1</version>
</dependency>
```  

3. 继续在pom.xml文件中加入以下内容用以添加[protobuf-maven-plugin](https://www.xolstice.org/protobuf-maven-plugin/)  
```
<build>
  <extensions>
    <extension>
      <groupId>kr.motd.maven</groupId>
      <artifactId>os-maven-plugin</artifactId>
      <version>1.4.1.Final</version>
    </extension>
  </extensions>
  <plugins>
    <plugin>
      <groupId>org.xolstice.maven.plugins</groupId>
      <artifactId>protobuf-maven-plugin</artifactId>
      <version>0.5.0</version>
      <configuration>
        <protocArtifact>com.google.protobuf:protoc:3.1.0:exe:${os.detected.classifier}</protocArtifact>
        <pluginId>grpc-java</pluginId>
        <pluginArtifact>io.grpc:protoc-gen-grpc-java:1.0.1:exe:${os.detected.classifier}</pluginArtifact>
      </configuration>
      <executions>
        <execution>
          <goals>
            <goal>compile</goal>
            <goal>compile-custom</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```  

4. 将target文件中生成的jar包加入Referenced Libraries即可  