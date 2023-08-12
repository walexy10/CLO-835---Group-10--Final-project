# CLO-835---Group-10--Final-project

Create ECR repositories and the security group using either the terraformCode folder or manually from the AWS console
Create a private s3 bucket in the AWS console and add some imagesin the bucket
The app WAS RUN locally first, then as containers and then on the EKS cluster
Use the docker build command to build the database application from within the database folder. This db container needs to be running in the background for the app to work.
To run the app locally, update app.py with your aws credentials, install the requirements and use “python app.py” to run the flask application. Use the public IP:Port of the cloud9 instance to access the web app. Here we use Port=81. The db container needs to be running in the background for the app to work.
Use the docker build command to build the webapp application from within the webApp folder. Ensure environment variables are passed along for the app to work. Use the public IP:Port of the cloud9 instance to access the web app.
Set up the EKS cluster using the files in the EKS cluster folder. You may need to chmod the files or update the aws credentials
Use kubectl apply on the yaml files to set up the pods, the services and the deployment.
The application can be accessed from the public IP of the EC2 instance once the loadBalancer has been exposed. You may need to modify the security group to achieve this.Use the public IP:Port of the ec2 instance to access the web app or use port-forwarding
When running locally
##install the required MySQL package

Building and running 2 tier web application locally
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
export GROUPNAME='group5jaas'
export objectName='jello.jpg'
Run the application, make sure it is visible in the browser
docker run -p 81:81  -e DBHOST=$DBHOST -e DBPORT=$DBPORT -e  DBUSER=$DBUSER -e DBPWD=$DBPWD -e GROUPNAME=$GROUPNAME -e objectName=$objectName  app
