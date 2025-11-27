# # Build stage
# FROM maven:3.9.11-eclipse-temurin-8 AS build
# WORKDIR /opt/server

# # Copy correct source code
# COPY ../SHIP-SRC/pom.xml .
# COPY ../SHIP-SRC/src ./src

# # Build the JAR
# RUN mvn clean package


# # Run stage
# FROM eclipse-temurin:8-jdk
# WORKDIR /opt/server
# COPY --from=build /opt/server/target/shipping-1.0.jar shipping.jar
# ENTRYPOINT ["java","-jar","shipping.jar"]
# EXPOSE 8080

# Dockerfile (inside SHIP-SRC)
FROM maven:3.9.11-eclipse-temurin-8 AS build
WORKDIR /opt/server

COPY pom.xml .
COPY src ./src

RUN mvn clean package

FROM eclipse-temurin:8-jdk
WORKDIR /opt/server
COPY --from=build /opt/server/target/shipping-1.0.jar shipping.jar
ENTRYPOINT ["java","-jar","shipping.jar"]
EXPOSE 8080