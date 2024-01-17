FROM ubuntu:24.04

WORKDIR /opt/dep

RUN apt update -y && apt install -y build-essential libz-dev zlib1g-dev wget

RUN wget https://github.com/graalvm/mandrel/releases/download/mandrel-23.0.2.1-Final/mandrel-java17-linux-amd64-23.0.2.1-Final.tar.gz
RUN tar -xf mandrel-java17-linux-amd64-23.0.2.1-Final.tar.gz

# RUN wget https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz
# RUN tar -xzf apache-maven-3.9.6-bin.tar.gz

ENV JAVA_HOME="/opt/dep/mandrel-java17-23.0.2.1-Final"
ENV GRAALVM_HOME="${JAVA_HOME}"
ENV PATH="${JAVA_HOME}/bin:${PATH}"
# ENV PATH="./apache-maven-3.9.6/bin:${PATH}"

WORKDIR /opt/app

COPY src .
COPY pom.xml .
COPY .mvn .mvn
COPY mvnw .

RUN ./mvnw clean package -Dquarkus.package.type=uber-jar

EXPOSE 8080

CMD ["java", "-jar", "/opt/app/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar"]