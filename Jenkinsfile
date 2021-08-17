pipeline {
  agent any
  stages {
    stage('stop last container and delete last image') {
      steps {
        script {
          sh '''docker ps -q | xargs docker stop \$
          docker ps -a | grep golang-http-server | xargs -n 1 -r docker rm \$
          docker images | grep golang-http-server | xargs -n 2 -r docker rmi'''
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
