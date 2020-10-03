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

    stage('Build docker image') {
      steps {
        echo 'Deploy'
        sh 'sudo docker build . -t coustomnginx:1'
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
}