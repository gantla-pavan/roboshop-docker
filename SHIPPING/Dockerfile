FROM maven:3.9.11 AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src ./src
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar
    ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="MYSQL" 
     CMD ["java","-jar","shipping.jar"]