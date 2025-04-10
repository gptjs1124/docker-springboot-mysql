FROM mysql:8.0
# mysql:8.0 이미지를 가지고 온다.

COPY init.sql /docker-entrypoint-initdb.d
# init.sql파일을 컨테이너의 특정 디렉토리인 /docker-entrypoint-initdb.d로 복사하는 역활

# init.sql파일은 보통 데이터베이스 초기화 쿼리 또는 스크립트가 포함되어 있는 파일

# /docker-entrypoint-initdb.d
# Docker에서 MySQL, PostgreSQL과 같은 데이터베이스 이미지를 사용할 때 사용되는 특정 디렉토리입니다.
# 이 디렉토리에 있는 SQL 파일은 컨테이너가 처음 실행될 때 자동으로 실행됩니다. 즉, 데이터베이스가 시작될 때 init.sql 파일에 포함된 SQL 쿼리가 실행되어 초기 설정이 이루어집니다.

ENV MYSQL_ROOT_PASSWORD=root1234
ENV MYSQL_DATABASE=metadb
ENV MYSQL_HOST=%
# ENV는? Dockerfile에서 환경 변수를 설정하는 명령어입니다.

CMD ["--character-set-server=utf8mb4", "--collation-server=utf8mb4_unicode_ci"]
# "--character-set-server=utf8mb4" : utf8mb4는 UTF-8 문자 인코딩의 확장 버전으로, 4바이트로 구성된 모든 유니코드 문자를 지원
# "--collation-server=utf8mb4_unicode_ci" : utf8mb4_unicode_ci는 유니코드 규칙을 기반으로 하는 대소문자 구분 없는(cased insensitive) 정렬 방식입니다.