[Dockerfile 例(わかりやすい)](http://www.testautomationguru.com/jmeter-distributed-load-testing-using-docker/)  

[Docker compose 例1](https://github.com/pedrocesar-ti/distributed-jmeter-docker/blob/master/local/docker-compose.yml)

[Dockerfile 例1](https://github.com/pedrocesar-ti/distributed-jmeter-docker/blob/master/Dockerfile)

[Dockerfile 例2(How to Use the Docker Container with JMeter)](https://medium.com/@vinodkrane/how-to-use-the-docker-container-with-jmeter-5dbf47aaa26d)  
Jmeterのインストールはこちらを参考にしている

```
# build on the top of Java image
FROM java:8
# JMeter Version
ARG JMETER_VERSION=”5.3"
# Download and unpack the JMeter tar file
RUN cd /opt \
 && wget https://mirrors.estointernet.in/apache//jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz \
 && tar xzf apache-jmeter-${JMETER_VERSION}.tgz \
 && rm apache-jmeter-${JMETER_VERSION}.tgz
# Create a symlink to the jmeter process in a normal bin directory
RUN ln -s /opt/apache-jmeter-${JMETER_VERSION}/bin/jmeter /usr/local/bin
# Copying custom property file
COPY user.properties /opt/apache-jmeter-${JMETER_VERSION}/bin/user.properties
# Indicate the default command to run
CMD jmeter
```

[Dockerfile 例3(Ubuntu 20.04 GUI版JMeterをDockerで起動する)](https://knkomko.hatenablog.com/entry/2021/06/07/221638)

[実際に利用しているDockerベースイメージはopenjdk](https://hub.docker.com/_/openjdk?tab=tags&page=1&name=11-s)

[JMeter と Docker を使用した分散テスト](https://engineering.99x.io/distributed-testing-using-jmeter-docker-70c054a94fce)  
あんま参考にならなさそう

[Docker jmeterコマンド例](https://github.com/vmarrazzo/docker-jmeter/blob/jmeter_4_0_rmi_secure/docker_distributed_jmeter.sh)
- docker-composeの参考にも(https://github.com/vmarrazzo/docker-jmeter/blob/master/docker-compose.yml)
- 親ページ[JMeter Distributed Testing with Docker](https://www.blazemeter.com/blog/jmeter-distributed-testing-with-docker)

