# mnist-project

项目简介：将MNIST应用部署到容器里面，用户通过curl -XPOST命令提交带有手写体的数字图片，通过程序先将图片识别出来，然后将识别出的数字返回给用户。对MNIST中用户每次提交的图片、识别的文字和时间戳信息，都要记录到Cassandra以内进行存储。

项目工具：docker，cassandra，mnist，tensorflow

项目步骤：
1.创建网络

docker network create mnist_test

2.启动cassandra，并将其与docker连接

docker run --name mnist_cassandra --net=mnist_test -p 9042:9042 -d cassandra:latest

3.创建镜像

docker built -t mnist .

4.运行镜像

docker run -p 4000:2500 --network=mnist_test mnist

5.启动cassandra，并用cql语言查看数据库内容

docker exec -it mnist_cassandra cqlsh

use mnistimages;

select * from images;
