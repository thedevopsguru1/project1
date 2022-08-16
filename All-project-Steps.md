
# what do you need to automate CI and CD an application?
## I- Installing jenkins:
### After testing the code locally , the second thing to do is to setup your Jenkins pipeline.
### 1- Setup Jenkins pipeline:
#### - Install jenkins on a server 
### 2 - Steps to install jenkins : 
#### - Install jenkins Dependencies: Java JDK & JAVA JRE
#### - Download Jenkins binaries from Jenkins.io
#### - Install and Start Jenkins
https://github.com/devopstrainingschool/Jenkins-installation-steps

## II- CI
### When the developer pushes the code, jenkins will pull that code.
### Jenkins compile the code , and test it with Sonarqube, then build and push the docker image to the artifactory(docker hub).
## In order to archive this:
#### - we need to identify the type of application: Java Application , & maven compiler
#### - Build a Jenkinfile: 
https://github.com/devopstrainingschool/java-maven-app-project/blob/main/Jenkinsfile
#### - Install git : yum install git -y
#### - Install Docker
https://github.com/devopstrainingschool/docker-installation
#### - Go to Jenkins server, and create a pipeline Job.
#### - Setup maven-yaya tool: 
#### - Installing plugins: git , docker, maven
#### - We run our pipeline to make sure that maven is working properly
#### - Install Sonarqube Server
https://github.com/devopstrainingschool/sonarqube-installation
#### - Integrate Sonarqube with Jenkins
https://github.com/devopstrainingschool/sonarqube-jenkins-integration
##### - Go to Jenkins and Install sonarqube plugins
##### - GO to Jenkinsfile and add Sonarqube stages
##### - Run the Jenkins pipeline again
##### - Add docker build and docker push in the Pipeline.
##### - We need to add docker hub (artifactory ) credentials
##### - Run the Jen kins pipeline again
##### - the pipeline may failed : run this command
```
chown jenkins:docker  /var/run/docker.sock
```
##### - Then re run the pipeline
## III- Webhook between Github and Jenkins
### 1- Go to the Jenkins Job (project1), then click on configure, then look for build triggers, finally click on " GitHub hook trigger for GITScm polling"
### 2- go Github , then click on the project repository, click on settings, click webhooks, then click on add a webhook
### payload = jenkins_url(ip address)/github-webhook/
![image](https://user-images.githubusercontent.com/107158398/184759249-b3f1f524-a272-417c-8487-bc0e0067c80c.png)




