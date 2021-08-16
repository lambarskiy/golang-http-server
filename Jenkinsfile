pipeline {
  agent any
  environment {
    CURRENT_BRANCH_NAME = "${env.BRANCH_NAME}"
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
          sh 'echo $CURRENT_BRANCH_NAME > /var/tmp/branch.var'
        }
      }
    }
  }
}
