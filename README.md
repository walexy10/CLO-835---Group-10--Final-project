# CLO-835---Group-10--Final-project

This repository contains the code and configuration for the CLO835 Final Project, which involves deploying a 2-tiered web application to a managed Kubernetes cluster on Amazon EKS, with pod auto-scaling and deployment automation.

**Overview**

The Final Project aims to enhance an existing web application, build and deploy Docker images, create an Amazon EKS cluster, and deploy the application using Kubernetes manifests. The project also includes optional tasks such as deployment automation using Flux and implementing auto-scaling.

**##install the required MySQL package**

**Building and running 2 tier web application locally**

Building mysql docker image

docker build -t my_db -f Dockerfile_mysql . 

Building application docker image

docker build -t my_app -f Dockerfile . 

Running mysql

docker run -d -e MYSQL_ROOT_PASSWORD=pw  my_db

Get the IP of the database and export it as DBHOST variable

docker inspect <container_id>

Example when running DB runs as a docker container and app is running locally
export DBHOST=127.0.0.1
export DBPORT=3307
Example when running DB runs as a docker container and app is running locally
export DBHOST=172.17.0.2
export DBPORT=3306
export DBUSER=root
export DATABASE=employees
export DBPWD=pw
export APP_COLOR=blue
export GROUPNAME='group10'
export objectName=''

Run the application, make sure it is visible in the browser
docker run -p 81:81  -e DBHOST=$DBHOST -e DBPORT=$DBPORT -e  DBUSER=$DBUSER -e DBPWD=$DBPWD -e GROUPNAME=$GROUPNAME -e objectName=$objectName  app
