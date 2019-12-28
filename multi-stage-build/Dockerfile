FROM alpine/git AS HEAVY-DOWNLOADER
WORKDIR /app
CMD git clone https://github.com/ndekwe/building-docker-images.git
CMD cd building-docker-images/multi-stage-build


FROM maven:3.5.2-jdk-8-alpine AS MEDIUM-BUILDER
WORKDIR /app
COPY . /app
CMD mvn install

FROM openjdk:8-alpine AS LIGHT-DEPLOYER
COPY --from=MEDIUM-BUILDER /app/target/multi-stage-build-1.0-SNAPSHOT.jar .
EXPOSE 8089
CMD java -jar multi-stage-build-1.0-SNAPSHOT.jar

