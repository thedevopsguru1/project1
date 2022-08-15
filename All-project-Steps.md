
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
#### - Go to Jenkins server, and create a pipeline Job.
#### -

