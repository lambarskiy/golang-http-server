pipeline {
  agent any
  stages {
    stage('delete last image') {
      steps {
        script {
          sh 'printenv'
        }
      }
    }
  }
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
          sh 'export $BRANCH_NAME'
        }
      }
    }
  }
}
