pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        script {
          sh 'docker build -t golang-http-server:${BRANCH_NAME} .'
        }
      }
    }
    stage('cleanup') {
      steps {
        script {
          sh 'yes | docker container prune'
          sh 'yes | docker image prune'
        }
      }
    }
    stage('set environmental variable') {
      steps {
        script {
          sh 'set BRANCH_NAME=${BRANCH_NAME}'
        }
      }
    }
  }
}
