# Java 기반의 Docker 이미지 사용
FROM eclipse-temurin:17-jdk-alpine

# 작업 디렉토리 설정
WORKDIR /GongstaBackEnd

# 빌드된 JAR 파일 복사
COPY target/app.jar app.jar

# 애플리케이션 실행
ENTRYPOINT ["java", "-jar", "app.jar"]
