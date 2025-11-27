# FROM maven:3.9.11 AS builder
# EXPOSE 8080
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package && \
#     mv target/shipping-1.0.jar shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java","-jar","shipping.jar"]


# # Use Maven to build the project
# FROM maven:3.9.11 AS builder

# WORKDIR /opt/server

# # Copy pom.xml and source
# COPY pom.xml .
# COPY src ./src

# # Build the JAR
# RUN mvn clean package

# FROM eclipse-temurin:8-jdk

# WORKDIR /opt/server

# # Copy the JAR from builder stage
# COPY --from=builder /opt/server/target/shipping-1.0.jar shipping.jar

# # Set environment variable for CART service
# ENV CART_ENDPOINT="cart:8080"

# # Expose port 8080
# EXPOSE 8080

# # Run the app
# CMD ["java", "-jar", "shipping.jar"]

# # Build stage
# FROM maven:3.9.11-eclipse-temurin-8 AS build
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package

# # Run stage
# FROM eclipse-temurin:8-jdk
# WORKDIR /opt/server
# COPY --from=build /opt/server/target/shipping.jar shipping.jar
# EXPOSE 8080
# CMD ["java", "-jar", "shipping.jar"]

# Build stage
# FROM maven:3.9.11-eclipse-temurin-8 AS build
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package

# Run stage
FROM eclipse-temurin:8-jdk
WORKDIR /opt/server
COPY --from=build /opt/server/target/shipping-1.0.jar shipping.jar
EXPOSE 8080
CMD ["java", "-jar", "shipping.jar"]


# Build stage
FROM maven:3.9.11-eclipse-temurin-8 AS build
WORKDIR /opt/server

# Copy the actual source code
COPY ../SHIP-SRC/pom.xml .
COPY ../SHIP-SRC/src ./src

# Build the JAR
RUN mvn clean package






