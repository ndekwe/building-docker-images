#Download an image in which java version 8 is installed
FROM java:8
# Setting the work directory as “/”
WORKDIR /
#Copying files to the working directory
ADD . . 
# Setting the application network port as 8089
EXPOSE 8089
# Executing the program to spin up the web server
CMD java WebServer 

