

# Vincent:
## We have a project. 
###  1- developers will write the code ( java, nodejs, python , go , so on): java
### 2- if you have a Java application, you need to know the compiler(maven, gradle): maven
### 3- you may need to ssh to a server ( test) or if you have mac book then you can use it.
### 4- we want ask how to application is running to the developers.
### 5- Do we need a database? Yes
### 6- What database to use? mongodb
### 7- How the application will connect to the database?( environment: URL(host), username, password, database_name)
### 8- Go to hub.docker.com and look how to use the database ( mongo, mysql, mariadb, postgres): Look for docker-compose
![image](https://user-images.githubusercontent.com/107158398/183540316-a4c6db44-b2a7-4610-9f00-4a72bef2428f.png)

### 9- We went to the company github , and into the project , we created docker-compose.yaml
```
version: "3"
services:
   webapp:
     image: knote
     environment:
       - MONGO_URL=mongodb://mongo:27017/dev
     depends_on:
       - mongo
     ports:
       - "8080:8080"
   mongo:
     image: mongo
     ports:
       - "27017:27017"
```
#### - we did a pull request to merge the changes 
### 10 - On the server or the mac book:
#### - install git ( to clone our repo locally)
#### - install java 
#### - Install maven
#### - we run the commands:
```
mvn clean
```
```
mvn package
```
```
docker build -t knote .
```
#### - docker images ( to make sure we have the image called knote)
```
docker images
```
#### - we run this command:
```
docker compose up -d
```
#### - we run 
```
docker ps
```
## to make sure the application is running.
![image](https://user-images.githubusercontent.com/107158398/183541122-475197b2-3b5d-4055-a442-f8307f1b8ff8.png)

## Now to access the application from the browser, we can use:
### * ipaddress:port if using a server
![image](https://user-images.githubusercontent.com/107158398/183541436-3216ab13-6b02-4a87-8b4d-6780505b381e.png)

### * localhost:port number of using mac book
![image](https://user-images.githubusercontent.com/107158398/183541521-180538e3-efa3-47ba-b27e-69cadbc27cfb.png)

## Then we are done testing locally . We can start building our CI /CD pipeline




