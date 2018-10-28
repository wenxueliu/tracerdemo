


[在线 demo](http://106.75.237.45:8080/#/trace)

## 安装 skywalking

### 手动

下载 skywalking

从 http://skywalking.apache.org/downloads/ 下载最新已编译版本，并解压

安装 elasticsearch

到 https://www.elastic.co/downloads/past-releases/elasticsearch-5-6-12 下载 elasticsearch

wget -c https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.4.2.deb

### 用 docker 

docker run -p 9200:9200 -p 9300:9300 -e cluster.name=elasticsearch -e xpack.security.enabled=false --name=elasticsearch --restart=always -d wutang/elasticsearch-shanghai-zone

http://localhost:9200/

docker run -p 8080:8080 -p 10800:10800 -p 11800:11800 -p 12800:12800 -e ES_CLUSTER_NAME=elasticsearch -e ES_ADDRESSES=127.0.0.1:9300 -d wutang/skywalking-docker:5.x

参考

https://www.itdks.com/eventlist/detail/2375
https://github.com/OpenSkywalking/Community
https://www.cnblogs.com/huangxincheng/p/9666930.html
https://github.com/JaredTan95/skywalking-docker
https://blog.csdn.net/jilo88/article/details/81355265
https://www.cnblogs.com/liguobao/p/9686310.html
