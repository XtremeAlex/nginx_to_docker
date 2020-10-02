pipeline {
  agent {
    docker {
      image 'mthenw/frontail'
      args '''--ip 172.17.0.8 -d -p 8087:9001 -P 
-v /var/log:/log  /log/syslog -url-path /syslog --disable-usage-stats'''
    }

  }
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build'
            sh 'docker run  --ip 172.17.0.8 -d -p 8087:9001 -P -v /var/log:/log mthenw/frontail /log/syslog -url-path /syslog --disable-usage-stats'
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
        sh 'docker run --rm -it -p 80:80 proxy_docker_nginx'
      }
    }

  }
}