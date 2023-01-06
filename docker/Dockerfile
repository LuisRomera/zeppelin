FROM ubuntu:20.04

RUN apt-get update && apt-get -y upgrade

RUN apt-get install -y openjdk-8-jdk

ENV JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/jre/"

RUN apt install -y maven

RUN apt install -y python3
RUN apt install -y pip

RUN apt install -y scala

RUN apt install -y wget

RUN apt-get install -y git

RUN wget https://downloads.apache.org/spark/spark-3.3.1/spark-3.3.1-bin-hadoop3-scala2.13.tgz
RUN tar xvf spark-*
RUN mv spark-3.3.1-bin-hadoop3-scala2.13 /opt/spark

ENV SPARK_HOME="/opt/spark/"
ENV PYSPARK_PYTHON="/usr/bin/python3"

RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1001 ubuntu
USER ubuntu
WORKDIR /home/ubuntu

RUN git clone https://github.com/LuisRomera/zeppelin


WORKDIR /home/ubuntu/zeppelin
RUN mvn clean install -DskipTests
RUN ./bin/zeppelin-daemon.sh start




EXPOSE 8080