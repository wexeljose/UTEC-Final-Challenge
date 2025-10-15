FROM openjdk:11-jre-slim

ENV JMETER_VERSION=5.6.3
ENV JMETER_HOME=/opt/apache-jmeter-${JMETER_VERSION}
ENV JMETER_BIN=${JMETER_HOME}/bin
ENV PATH=$PATH:${JMETER_BIN}

# Descargar e instalar JMeter
RUN apt-get update && apt-get install -y curl tar && \
    curl -L --silent https://archive.apache.org/dist/jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz \
        -o /tmp/apache-jmeter-${JMETER_VERSION}.tgz && \
    mkdir -p /opt && \
    tar -xzf /tmp/apache-jmeter-${JMETER_VERSION}.tgz -C /opt && \
    rm /tmp/apache-jmeter-${JMETER_VERSION}.tgz

# Copiar el Prometheus Listener
COPY jmeter-prometheus-listener.jar ${JMETER_HOME}/lib/ext/

EXPOSE 9270

WORKDIR ${JMETER_HOME}
ENTRYPOINT ["jmeter"]
