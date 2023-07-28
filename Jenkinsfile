pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        bat 'docker build -t marwenerzig1/jenkins-docker-hubb .'
      }
    }
    stage('Login') {
      steps {
        bat 'set DOCKERHUB_CREDENTIALS_USR=marwenerzig1'
        bat 'set DOCKERHUB_CREDENTIALS_PSW=mezomeinhouse'
        bat 'docker login -u="$DOCKERHUB_CREDENTIALS_USR" -p="$DOCKERHUB_CREDENTIALS_PSW"'
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
