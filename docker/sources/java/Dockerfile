FROM eclipse-temurin:21-jdk

ARG USER_ID=1000
ARG GROUP_ID=1000

RUN set -eux; \
    userdel -r ubuntu; \
    groupadd -g "${GROUP_ID}" app; \
    useradd -m -u "${USER_ID}" -g app app

WORKDIR /app
USER app

EXPOSE 8080

CMD ["./mvnw", "spring-boot:run"]
