
变量

* zipKinServer: zipKin 所在主机的 ip
* AppServer: webmvc-boot 所在的主机 ip

## 安装并启动 zipkin

docker run -d -p 9413:9411 openzipkin/zipkin

${zipKinServer} 的 9411 端口映射到容器的 9411 端口

## 编译例子 

### webmvc4-boot

Frontend 监听 8081 端口，Backend 监听 9000 端口，访问 Frontend，Frontend
访问 Backend 的 9000 端口，Backend 返回当前时间。

cd webmvc4-boot/

启动 Front

mvn compile exec:java -Dexec.mainClass=brave.webmvc.Frontend

启动 Backend

mvn compile exec:java -Dexec.mainClass=brave.webmvc.Backend

注：如果 ${zipKinServer} 与 ${AppServer} 不同时，修改 TracingConfiguration
中的 zipKinServer 变量为 ${zipKinServer}

## 验证

多次访问 http://${AppServer}:8081/

zipkin 服务 http://${zipKinServer}:9413/

