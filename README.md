# JBOSS EAP 7.1 [![Build Status](https://travis-ci.org/daggerok/jboss-eap-7.1.svg?branch=master)](https://travis-ci.org/daggerok/jboss-eap-7.1)

## DEPRECATED

### USE [daggerok](https://github.com/daggerok/jboss)/[jboss:eap-7.1](https://hub.docker.com/r/daggerok/jboss) instead

Docker hub automation build. Based on (Linux Alpine, OpenJDK 8u151) docker image: `openjdk:8u151-jdk-alpine`

**Exposed ports**:

- 8080 - deployed apps https port
- 9990 - console port
- 8443 - https port

**Console**:

- url: http://127.0.0.1:9990/console
- user: admin
- password: Admin.123

### Usage:

```

FROM daggerok/jboss:eap-7.1
ADD ./build/libs/*.war ${JBOSS_HOME}/standalone/deployments/

```


#### Usage with remote debug:

```

FROM daggerok/jboss:eap-7.1
RUN echo "JAVA_OPTS=\"\$JAVA_OPTS -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \"" >> ${JBOSS_HOME}/bin/standalone.conf
EXPOSE 5005
ADD ./build/libs/*.war ${JBOSS_HOME}/standalone/deployments/

```
