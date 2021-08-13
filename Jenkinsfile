pipeline {
  agent none
  stages {
    stage('build') {
      steps {
        script {
          sudo docker build -t golang-http-server:$BRANCH_NAME .
        }
      }
    }
  }
}
    






