FROM alpine/git AS HEAVY-DOWNLOADER
WORKDIR /app
#RUN git config --global http.proxy http://proxyuser:proxypwd@proxy.server.com:8080
RUN git config --global --unset http.proxy
#RUN git config --global --unset https.proxy
RUN set NO_PROXY=localhost
RUN git clone http://github.com/ndekwe/building-docker-images.git
CMD cd building-docker-images/multi-stage-build


FROM maven:3.5.2-jdk-8-alpine AS MEDIUM-BUILDER
WORKDIR /app
COPY --from=HEAVY-DOWNLOADER /app/building-docker-images/multi-stage-build /app
CMD mvn install

FROM openjdk:8-alpine AS LIGHT-DEPLOYER
COPY --from=MEDIUM-BUILDER /app/target/multi-stage-build-1.0-SNAPSHOT.jar .
EXPOSE 8089
CMD java -jar multi-stage-build-1.0-SNAPSHOT.jar

