FROM maven:3.8.6-openjdk-11-slim AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn package -DskipTests

FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8083
# Make sure Java is using the correct port that matches your .env file
ENV SERVER_PORT=8083
CMD ["java", "-jar", "-Dserver.port=8083", "app.jar"]
