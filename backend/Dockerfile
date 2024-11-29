# 1단계: Gradle 빌드 환경
FROM gradle:7.6-jdk17 AS builder
WORKDIR /app

# Gradle wrapper와 소스 코드 복사
COPY GongstaBackEnd/ /app/

# Gradle로 Spring Boot JAR 파일 빌드
RUN ./gradlew clean bootJar

# 2단계: JAR 실행 환경
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

# 빌드된 JAR 파일 복사
COPY --from=builder /app/build/libs/*.jar app.jar

# 애플리케이션 실행
ENTRYPOINT ["java", "-jar", "app.jar"]
