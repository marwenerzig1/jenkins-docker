pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-acces')
  }
  stages {
    stage('Build') {
      steps {
        bat 'docker build -t marwenerzig1/jenkins-docker-hubb .'
      }
    }
    stage('Login') {
      steps {
        echo 'Hello world'
      }
    }
    stage('Push') {
      steps {
        bat 'docker push marwenerzig1/jenkins-docker-hubb'
      }
    }
  }
  post {
    always {
      bat 'docker logout'
    }
  }
}
