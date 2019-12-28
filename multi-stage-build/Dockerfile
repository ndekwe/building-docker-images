#FROM alpine/git
#WORKDIR /app
#RUN git clone https://github.com/ndekwe/buildingDockerImages.git
#RUN cd multiStagesBuild

# To be continued: https://dzone.com/articles/a-dockerfile-for-maven-based-github-projects


#FROM maven as heavybuilder
FROM maven:3.5.2-jdk-8-alpine
#COPY pom.xml /tmp/
#COPY src /tmp/src
WORKDIR /app
#COPY pom.xml /app
#COPY src /app/src
#RUN mvn install
COPY . /app
CMD mvn install

FROM openjdk:8-alpine
#RUN mkdir /app
#WORKDIR /app
COPY --from=0 /app/target/multi-stage-build-1.0-SNAPSHOT.jar .
EXPOSE 8089
#ENTRYPOINT ["java", "-jar"]
#CMD ["/path-to-jar-file"]
# Executing the program using package.jar and directing the result in another file
#RUN java -jar multi-stage-build-1.0-SNAPSHOT.jar
CMD java -jar multi-stage-build-1.0-SNAPSHOT.jar
