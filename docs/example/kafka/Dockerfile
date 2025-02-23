FROM apache/kafka:3.9.0

USER root

# Add the Prometheus JMX exporter agent
ARG JMX_VERSION=1.0.1

ADD https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/${JMX_VERSION}/jmx_prometheus_javaagent-${JMX_VERSION}.jar /opt/kafka/

RUN mv /opt/kafka/jmx_prometheus_javaagent-${JMX_VERSION}.jar /opt/kafka/jmx_prometheus_javaagent.jar && \
	chown -R appuser:appuser /opt/kafka/

# Add the Prometheus JMX exporter configuration
RUN mkdir -p /opt/kafka/config

COPY jmx/config.yml /opt/kafka/config/jmx_exporter_config.yml

USER appuser
