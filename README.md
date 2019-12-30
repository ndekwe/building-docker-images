# Three ways to build Docker images
In this repository you will find the codes and images used to write a blog post related to three ways used to build docker images. Three folders of this projects, namely "[normal-build](https://github.com/ndekwe/building-docker-images/tree/master/normal-build)", "[buildFromPackage](https://github.com/ndekwe/building-docker-images/tree/master/buildFromPackage)" and "[multi-stage-build](https://github.com/ndekwe/building-docker-images/tree/master/multi-stage-build)", hold the codes used for each way. 

# 1. Building Docker image with a normal build
![alt text](images/normal-docker-build.png) 

To build the docker image with normal build, follow below steps: 

Step 1: Clone the project and access “normal-build” directory \
$ git clone https://github.com/ndekwe/building-docker-images.git \
$ cd building-docker-images/normal-build/

Check the Dockerfile under "building-docker-images/normal-build/" \
Step 2: Build the Dockerfile using the following command: \
$ docker image build -t web-server-docker-image . \
The image has built successfully: \
$ docker image ls | grep web-server-docker-image \
web-server-docker-image            latest               195d2421a637        57 seconds ago      643MB 

To run the web server container from the created image: \
$ docker run -p 127.0.0.1:80:8089 web-server-docker-image:latest 

Checking running containers: \
$ docker container ls \
To access the web server, you can run URL http://localhost/ or http://127.0.0.1/ in the browser. 

# 2. Building Docker image from a jar file
![alt text](images/docker-image-from-jar.png)

Use files under "building-docker-images/buildFromPackage/" to build from a jar file\ 

Step 1: Access “buildFromPackage” directory and compile the program\
$ javac WebServer.java

Step 2: Creating a “jar” file \
$ jar cvmf MANIFEST.MF webserver.jar WebServer.class

Building an image from the jar file:\
$ docker build -t web-server-docker-image-from-jar .

Once the build is done successfully, you can check the information about the image:\
$ docker image ls | grep web-server-docker-image-from-jar

You can run it in order to test the web server program:
$ docker run -p 127.0.0.1:80:8089 web-server-docker-image-from-jar:latest


# 3. Building Docker image with multi-stages build
![alt text](images/multi-stage-build.png)

For multi-stages build check files under "building-docker-images/multi-stage-build/"

Run the following command: \
$ docker build -t web-server-docker-image-multi-stage .

Listing images: \
$ docker image ls


