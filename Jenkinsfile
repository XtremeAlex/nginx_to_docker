pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Fetch Dependencies') {
          steps {
            echo 'Fetch Dependencies'
            sh 'sudo docker pull nginx:latest'
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
        input(message: 'Procedere Al Deploy?', id: 'OK')
        sh 'docker build -t nginx:alpine .'
      }
    }

  }
}