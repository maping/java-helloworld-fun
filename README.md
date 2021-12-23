# Azure Function Simple Sample：java-helloworld-fun

## 1. 创建项目
```console
$ mvn archetype:generate -DgroupId=com.mwit.javafun -DarchetypeGroupId=com.microsoft.azure -DartifactId=java-helloworld-fun -DarchetypeArtifactId=azure-functions-archetype -Dversion=1.0-SNAPSHOT  -DjavaVersion=8 -DinteractiveMode=false
```

## 2. 修改代码
```console
$ cd java-helloworld-fun
$ code Function.java
`@FunctionName("HelloWorld")`
$ code pom.xml
指定 functionAppName, Resource Group, region, os
```

## 3. 构建并本地测试
```console
$ mvn clean package
$ mvn azure-functions:run
$ curl http://localhost:7071/api/HelloWorld?name=Forrest
Hello, Forrest
$ curl -d "Forrest" http://localhost:7071/api/HelloWorld
Hello, Forrest
```

## 4. 部署到 Azure
```console
$ az login
修改 pom.xml，指定 Resource Group, region, os,
$ mvn azure-functions:deploy
$ curl https://java-helloworld-fun.azurewebsites.net/api/HelloWorld?name=Forrest
Hello, Forrest
$ curl -d "Forrest" https://java-helloworld-fun.azurewebsites.net/api/HelloWorld
Hello, Forrest
$ func azure functionapp logstream java-helloworld-fun --browser
```
