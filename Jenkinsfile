pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        script {
          sh 'docker build -t golang-http-server:1.0 .'
        }
      }
    }
  }
}
    






