# 1. 빌드 단계: Maven으로 jar 생성
FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn -B package -DskipTests

# 2. 실행 단계: 빌드된 jar만 복사하여 실행
FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app
COPY --from=build /app/target/yagan.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
