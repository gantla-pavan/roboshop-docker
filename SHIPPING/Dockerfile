# Stage 1: build
FROM maven:3.9.11 AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src ./src
RUN mvn clean package

# Stage 2: runtime
FROM openjdk:8-jdk
WORKDIR /opt/server
COPY --from=builder /opt/server/target/shipping-1.0.jar shipping.jar
EXPOSE 8080
CMD ["java", "-jar", "shipping.jar"]
