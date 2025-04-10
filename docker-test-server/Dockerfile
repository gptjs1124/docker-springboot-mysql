FROM openjdk:11-jdk-slim

WORKDIR /app

# COPY만 docker-compose 파일의 위치를 기반으로 작동함
# copy .은 Dockerfile기반으로 상단으로 올라가서 docker-test-server 전체를 보고 뒤에 있는
# .은 workdir에 작성된 /app으로 copy를 진행한다고 생각하면 됨.
COPY . .

# 개행문자 오류 해결 [unix와 window 시스템 차이]
RUN sed -i 's/\r$//' gradlew

# RUN은 현재 파일을 위치를 기반으로 작동함
RUN chmod +x ./gradlew # copy가 진행된 뒤 gradlew라는 실행 파일이 있는데, 이 실행 권한을 준다.
RUN ./gradlew clean build # gradlew를 빌드한다.(실행한다)

ENV JAR_PATH=/app/build/libs
RUN mv ${JAR_PATH}/*.jar /app/app.jar
# 빌드가 된 뒤, project jar폴더 안에 app/bild/libs jar파일을 도커안에 있는 /app/app.jar로 이름을 변경 한 뒤 옮긴다.
# 이걸 하는 이유는 entrypoint에서 실행하기 편하게 변경하는 것.

ENTRYPOINT ["java", "-jar", "-Dspring.profiles.active=prod", "app.jar"]
# entrypoint는? 컨테이너가 시작되면 어떤 명령이 실행될지를 지정하는 역할
# Spring Boot 애플리케이션을 실행하기 위한 명령을 정의합니다. 컨테이너가 시작될 때 java -jar /app/myapp.jar 명령이 실행됩니다.

## https://www.youtube.com/watch?v=uCRaB5ER3zI 9:53 부터