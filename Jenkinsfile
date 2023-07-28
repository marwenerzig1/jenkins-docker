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
        bat 'docker build -t marwenerzig1/jenkins-docker-hub .'
      }
    }
    stage('Login') {
      steps {
        bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        bat 'docker push marwenerzig1/jenkins-docker-hub'
      }
    }
  }
  post {
    always {
      bat 'docker logout'
    }
  }
}
