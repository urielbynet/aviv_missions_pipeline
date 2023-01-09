pipeline {
    agent any
    environment {
    NEXUS_CREDS = credentials('nexus-credentials-id')
    } 
    stages {
        stage('Build') {
            steps {
              script{
                docker.build("nginx_test")
              }  
            }
        }
        stage('Login') {
            steps {
                sh 'docker login -u $NEXUS_CREDS_USR -p $NEXUS_CREDS_PSW localhost:8081'
            }
            }
        stage('Push') {
            steps {
                sh 'docker push nginx_test'
            }
    }
  }

}
