FROM openjdk:11-slim-buster

ARG APP_ROOT=/var/jmeter

# JMeter version
ARG JMETER_VERSION=5.4.3

WORKDIR ${APP_ROOT}

RUN set -ex \
  && apt-get update && apt-get install -y --no-install-recommends \
    procps \
    curl \
    unzip \
    wget

# Download and unpack the JMeter tar file
RUN set -ex \
  && cd /opt \
  && wget https://archive.apache.org/dist/jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz \
  && tar xzf apache-jmeter-${JMETER_VERSION}.tgz \
  && rm apache-jmeter-${JMETER_VERSION}.tgz

# Create a symlink to the jmeter process in a normal bin directory
RUN ln -s /opt/apache-jmeter-${JMETER_VERSION}/bin/jmeter /usr/local/bin

ENTRYPOINT ["jmeter"]