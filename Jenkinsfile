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
        bat 'docker login -u="marwenerzig1" -p="mezomeinhouse"'
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
