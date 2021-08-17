pipeline {
  agent any
  stages {
    stage('stop last container and delete last image') {
      steps {
        script {
          sh 'docker ps -a | grep golang-http-server | xargs -r docker stop 2> /dev/null'
          sh 'docker ps -a | grep golang-http-server | xargs -r docker rm 2> /dev/null'
          sh 'docker images | grep golang-http-server | xargs -r docker rmi 2> /dev/null'
        }
      }
    }
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
          sh 'yes | docker image prune'
        }
      }
    }
  }
}
