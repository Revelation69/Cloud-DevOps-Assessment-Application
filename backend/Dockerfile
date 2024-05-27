# Stage 1: Build the application
FROM maven:3.8.1-openjdk-11 AS build
WORKDIR /app

# Copy pom.xml and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Copy the source code and the frontend files
COPY src ./src
COPY package.json package-lock.json webpack.config.js ./

# Run npm install and build the frontend
RUN mvn clean package -DskipTests

# Stage 2: Create the runtime image
FROM openjdk:11-jre-slim
WORKDIR /app

# Copy the built jar file from the build stage
COPY --from=build /app/target/react-and-spring-data-rest-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080 and run the application
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
