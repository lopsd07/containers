FROM eclipse-temurin:21-jre-alpine

ARG APP_VER=5.6.3

ARG DOWNLOADS_URL="https://dlcdn.apache.org/jmeter/binaries/apache-jmeter-${APP_VER}.tgz"
ARG TARGETARCH

ENV BASE_DIR=/app
ENV JMETER_HOME=${BASE_DIR}/apache-jmeter-${APP_VER}
ENV PATH=$PATH:$JMETER_HOME/bin
ENV HOME="$BASE_DIR/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_NAME="linux"

WORKDIR $BASE_DIR

LABEL org.opencontainers.image.base.name="eclipse-temurin:8-jre-alpine" \
      org.opencontainers.image.description="JMeter image packaged by Bitlychee." \
      org.opencontainers.image.documentation="https://github.com/bitlychee/containers/tree/main/bitlychee/jmeter/README.md" \
      org.opencontainers.image.ref.name="jmeter" \
      org.opencontainers.image.source="https://github.com/bitlychee/containers/tree/main/bitlychee/jmeter" \
      org.opencontainers.image.title="jmeter" \
      org.opencontainers.image.version="1.0.0"


# Install necessary dependencies
RUN apk add --no-cache \
    curl \
    unzip \
    bash

# Download and extract JMeter
RUN curl -O ${DOWNLOADS_URL} && \
    tar -xzf apache-jmeter-${APP_VER}.tgz && \
    rm apache-jmeter-${APP_VER}.tgz

USER 1001
CMD ["jmeter", "-n", "-t", "/data/testplant.jmx"]
