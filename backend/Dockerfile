# 1단계: Gradle 빌드 환경
FROM arm64v8/openjdk:17-jdk-slim AS builder
WORKDIR /app

# Git 설치 (Raspberry Pi와 같은 ARM 환경에서도 동작하도록)
RUN apt-get update && apt-get install -y git && rm -rf /var/lib/apt/lists/*

# 프로젝트를 GitHub에서 클론
RUN git clone https://github.com/gongnol-i/GongstaBackEnd.git .

# Gradle wrapper에 실행 권한 추가
RUN chmod +x ./gradlew

# Gradle로 Spring Boot JAR 파일 빌드
RUN ./gradlew clean bootJar --no-daemon --info

# 2단계: JAR 실행 환경
FROM arm64v8/openjdk:17-jdk-slim
WORKDIR /app

# 빌드된 JAR 파일 복사
COPY --from=builder /app/build/libs/*.jar app.jar

# 애플리케이션 실행
ENTRYPOINT ["java", "-jar", "app.jar"]
