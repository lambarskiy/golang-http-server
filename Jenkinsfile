pipeline {
  agent any
  stages {
    stage('stop last container and delete last image') {
      steps {
        script {
          sh 'docker ps -a | grep golang-http-server | xargs -r docker stop'
          sh 'docker ps -a | grep golang-http-server | xargs -r docker rm'
          sh 'docker images | grep golang-http-server | xargs -r docker rmi'
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
