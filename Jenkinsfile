pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build'
            sh 'docker build -t proxy_docker_nginx .'
          }
        }

        stage('Test') {
          steps {
            echo 'Test'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploy'
      }
    }

  }
}