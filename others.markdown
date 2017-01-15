---
layout: page
title:  "Other"
date:   2017-01-01 10:09:27 +0100
categories: docker spring-profile
---

# Notes to be categorized

Spring Docker + profiles
https://spring.io/guides/gs/spring-boot-docker/

Dockerfile:
FROM frolvlad/alpine-oraclejdk8:slim
VOLUME /tmp
ADD gs-spring-boot-docker-0.1.0.jar app.jar
RUN sh -c 'touch /app.jar'
ENV JAVA_OPTS=""
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]

docker run -e "SPRING_PROFILES_ACTIVE=prod" -p 8080:8080 -t springio/gs-spring-boot-docker

## Spring profiles

Spring Boot: common application properties
http://docs.spring.io/autorepo/docs/spring-boot/current/reference/html/common-application-properties.html

Spring Profiles and external configuration
http://docs.spring.io/autorepo/docs/spring-boot/current/reference/html/boot-features-external-config.html#boot-features-external-config-profile-specific-properties
+ consider:
https://www.mkyong.com/spring/spring-profiles-example/


## Creating UML diagrams
[Plantuml]: http://plantuml.com/sequence-diagram
Plantuml

