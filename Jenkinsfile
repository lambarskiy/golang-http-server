pipeline {
  options { 
    disableConcurrentBuilds() 
  }
  agent any
  stages {
    stage('stop last container and delete last image') {
      steps {
        script {
          try { 
            sh 'docker ps -q | xargs docker stop'
          } 
          catch (err) {
            echo "No running container"
          }
          try { 
            sh 'docker ps -q | xargs docker rm'
          } 
          catch (err) {
            echo "No running container"
          }
          try { 
            sh 'docker images | grep golang- | xargs -n 2  echo | grep golang- | tr " " ':' | xargs docker rmi '
          } 
          catch (err) {
            echo "No latest image"
          }
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
          sh 'yes | docker container prune'
        }
      }
    }
  }
}
