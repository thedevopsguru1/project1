pipeline {
agent any
  tools {
    maven "maven-yaya"
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
        
    
    
  }
}
