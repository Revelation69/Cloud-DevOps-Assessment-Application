# Stage 1: Create the runtime image
FROM openjdk:11-jre-slim
WORKDIR /app

# Copy the built jar file from the pipeline workspace
COPY target/react-and-spring-data-rest-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080 and run the application
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
