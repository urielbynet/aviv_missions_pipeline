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
                sh 'docker login -u $NEXUS_CREDS_USR -p $NEXUS_CREDS_PSW localhost:8082'
            }
            }
        stage('Push') {
          steps {
                withDockerRegistry([ credentialsId: "nexus-credentials-id", url: "http://localhost:8082" ]) {
                sh 'docker tag nginx_test localhost:8082/nginx_test'
                sh 'docker push localhost:8082/nginx_test'   
            }
          }
    }
  }

}
