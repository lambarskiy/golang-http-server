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
    stage('run ansible playbook') {
      steps {
        dir("${PWD}") {
          ansiblePlaybook([
            inventory   : 'hosts',
            playbook    : 'golang_container_run.yaml',
            installation: 'ansible',
            colorized   : true,
            extraVars   : [
              pass_branch_name: env.BRANCH_NAME,
            ]
          ])
        }
      }
    }
  }
}
