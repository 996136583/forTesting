# Maven入门

![](https://img-blog.csdnimg.cn/20200728212538412.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZpbGxpbmdfbA==,size_16,color_FFFFFF,t_70)

##### 优点

1. 依赖管理：maven工程中不直接将jar包导入到工程中，而是通过在pom.xml文件中添加所需jar包坐标，这样就可以很好的避免了jar直接引进进来，在需要用到jar包的时候只需要找pom.xml，然后到一个专门存放jar包的仓库中根据坐标找这些jar包。

   ```mermaid
   graph LR
   A[本地] -->B(本地库)
   B --> C{是否存在远程库}
       C -->|存在| D[远程库]
       C -->|不存在| E[中央库]
       D --> |远程库中没有所需jar包|E
   F[maven仓库]
   
   ```

2. Maven清晰的结构

![img](https://img-blog.csdn.net/201808131239225?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvdmVxdWFucXVxbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

3. 跨平台
4. 协同开发

##### 坐标

```
<dependency>
   <groupId>cn.missbe.web.search</groupId>
   <artifactId>resource-search</artifactId>
   <packaging>jar</packaging>
   <version>1.0-SNAPSHOT</version>
</dependency>
```

在Maven中，坐标是Jar包的唯一标识，Maven通过坐标在仓库中找到项目所需的Jar包。

- **groupId**:所需Jar包的项目名
- **artifactId**:所需Jar包的模块名
- **version**:所需Jar包的版本号

## Maven基本命令

-v:查询Maven版本 本命令用于检查maven是否安装成功。

clean周期

mvn clean:删除target文件夹

default周期

mvn compile：编译   将java源文件编译成class文件

mvn test-compile：编译test目录下文件

mvn test:测试项目   执行test目录下的测试用例

mvn package:打包  将项目打成jar包

mvn install:安装  将当前项目放到Maven的本地仓库中。供其他项目使用

compile --> test-conpile --> test--> package-->install  **执行install会执行前面所有步骤 以此类推**

