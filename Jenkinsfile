pipeline {
  agent {
    kubernetes {
      yamlFile 'demo.yaml'
      idleMinutes 1
    }
  }
  stages {
    stage('Build maven code') {
      steps {
      container('mavencontainer') {  
          sh "mvn clean package"
       }    
      }
    }
    stage('Build docker image') {
      steps {
        container('dockercontainer') {
           
          sh '''
          
          docker build -t aksimage123.azurecr.io/demoapp:v1 .
          
          '''
          
        }
      }
    }
  }
}
