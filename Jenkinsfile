pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Fetch Dependencies') {
          steps {
            echo 'Fetch Dependencies'
            sh '''
docker build -t test-app:${BUILD_NUMBER} . '''
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
        input(message: 'Procedere Al Deploy?', id: 'OK')
        echo 'Deploy...'
        sh 'sudo docker run --rm -it -p 80:80 proxy_docker_nginx'
      }
    }

  }
  environment {
    HOME = '.'
  }
}