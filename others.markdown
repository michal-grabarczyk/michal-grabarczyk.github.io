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

## T420 TrackPoint Linux Change speed
[source]:https://bbs.archlinux.org/viewtopic.php?id=199998

* /etc/udev/rules.d/99-trackpoint.rules
{% highlight bash %}
KERNEL=="serio2", SUBSYSTEM=="serio", DRIVER=="psmouse", ATTR{speed}="200", ATTR{sensitivity}="255"
{% endhighlight %}

* /etc/systemd/system/trackpoint.service

{% highlight bash %}
[Unit]
Description=Set TrackPoint attributes

[Service]
Type=oneshot
ExecStartPre=/usr/bin/sleep 5
ExecStart=/usr/bin/udevadm trigger --subsystem-match=serio
ExecStartPost=/usr/bin/udevadm info -a -p /sys/devices/platform/i8042/serio1/serio2/

[Install]
WantedBy=multi-user.target
{% endhighlight %}
