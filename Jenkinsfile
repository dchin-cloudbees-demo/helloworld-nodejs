pipeline {
  kubernetes {
    label 'nodejs-app-pod'
    yamlFile 'nodejs-pod.yaml'
  }  
  options { 
    buildDiscarder(logRotator(numToKeepStr: '5'))
    skipDefaultCheckout true
  } 
  stages {
    stage('Test') {
      steps {
        sh 'java -version'
        container('nodejs') {
          echo 'Hello World!'   
          sh 'node --version'
        }
      }
    }
    
    stage('David stage') {
      steps {
        checkout scm
        echo 'David was here!'
      }
    }
    
    stage('Build and Push Image') {
      when {
         beforeAgent true
         branch 'master'
      }
      steps {
         echo "TODO - build and push image"
      }
    }
    
  }
}
