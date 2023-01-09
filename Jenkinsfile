pipeline {
    agent any
    environment {
    NEXUS_CREDS = credentials('nexus-credentials-id')
    SSH_TO_HOST = credentials('ssh_to_host')
    } 
    stages {
        stage('Build') {
            steps {
              script{
                docker.build("nginx_test")
              }  
            }
        }
        stage('SSH Conection') {
            steps {
                sh '''
                     sshpass -p $SSH_TO_HOST_PSW ssh -tt urielwo@192.168.103.161
                     docker login -u $NEXUS_CREDS_USR -p $NEXUS_CREDS_PSW localhost:8082
                   '''
            }
            }
        stage('Login') {
            steps {
                sh 'docker login -u $NEXUS_CREDS_USR -p $NEXUS_CREDS_PSW localhost:8082'
            }
    }
  }

}
