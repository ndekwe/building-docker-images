#Download an image in which java version 8 is installed
FROM java:8
# Setting the working directory
WORKDIR /
#Copying webserver jar package to the working directory mentioned above
# Note that it's only the packaged jar file which is copied.
ADD webserver.jar webserver.jar
# Setting the application network port
EXPOSE 8089
# Executing the program using packaged JAR file
CMD java -jar webserver.jar
