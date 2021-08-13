pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        script {
          sh 'sudo docker build -t golang-http-server:${BRANCH_NAME} .'
        }
      }
    }
  }
}
    






