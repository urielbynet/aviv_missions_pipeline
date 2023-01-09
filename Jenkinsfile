pipeline {
    agent any
    stages {
        stage('build') {
            steps {
              sh '''
                echo 'build started'
                docker build --tag nginx_app .
                docker images
              '''
            }
        }
      stage('push') {
            steps {
                sh 'docker push nginx_app'
            }
        }
    }
}