pipeline {
agent any
  tools {
    maven "maven-yaya"
  }
  environment {
        
        IMAGE_TAG = "${BUILD_NUMBER}"
   
        }
  stages {
    
    stage ('Maven Clean'){
      steps{
        sh 'mvn clean'
      }
    }
    stage ('Maven package') { 
      steps{
        sh 'mvn package'
      }
    }
    stage ('Sonarqube analysis and testing app'){
      steps{
        script{
          withSonarQubeEnv('sonarserver'){
            sh 'mvn clean package sonar:sonar'
          }
        }
      }
    }    
   stage ("Quality Gate Check") {
      steps {
        script {
           timeout(time: 1, unit: 'HOURS') { 
        def qg = waitForQualityGate() 
        if (qg.status != 'OK') {
             error "Pipeline aborted due to quality gate failure: ${qg.status}"
        }
           }
        }
      }
    }
    stage ('Docker build and push'){
   
           steps{
             withDockerRegistry([ credentialsId: "Docker_creds", url: "https://index.docker.io/v1/" ]){
               sh 'docker build -t devopstrainingschool/knote-jenkins:$BUILD_NUMBER . -f Dockerfile'
               sh 'docker push devopstrainingschool/knote-jenkins:$BUILD_NUMBER'
               sh 'rm -rf k8s-all-p1'
             }
           }
    }
    
 stage('Github clone the k8s-yaml'){
            steps {
                script{
                  catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
              sh "git clone https://github.com/devopstrainingschool/k8s-all-p1.git"
              
            
             
                    }
                  }
                }
            }
        }
  stage('Make yaml files changes & push them to Guthub'){
            steps {
                script{
                  catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    
                     sh """
                    git config --global user.name "devopstrainingschool"
                    git config --global user.email "devopstrainingschool@gmail.com" """
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                      dir('k8s-all-p1'){
                        sh "pwd"
                        sh "echo $BUILD_NUMBER"
                        sh "cat k8s/webapp.yaml"
                        sh "sed -i -e 's+knote-jenkins.*+knote-jenkins:${env.BUILD_NUMBER}+g'  k8s/webapp.yaml"
                        sh "cat k8s/webapp.yaml"
                        sh " git add . "
                        sh " git commit -m 'Updated the deployment file'"
                        sh "git push http://$GIT_USERNAME:$GIT_PASSWORD@github.com/devopstrainingschool/k8s-all-p1.git master"
             
                      }
             
                    }
                  }
                }
            }
        }
    

    
    
    
  }
}

