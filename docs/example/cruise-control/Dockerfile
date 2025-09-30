FROM gradle:jdk21-alpine

RUN apk add --no-cache \
	bash \
	curl \
	git

ARG CRUISE_CONTROL_VERSION=3.0.3
RUN git clone --branch ${CRUISE_CONTROL_VERSION} https://github.com/linkedin/cruise-control.git /opt/cruise-control

WORKDIR /opt/cruise-control

RUN ./gradlew jar copyDependantLibs

COPY config/cruisecontrol.properties /opt/cruise-control/config/cruisecontrol.properties

EXPOSE 8899

ENTRYPOINT ["/opt/cruise-control/kafka-cruise-control-start.sh", "/opt/cruise-control/config/cruisecontrol.properties"]
