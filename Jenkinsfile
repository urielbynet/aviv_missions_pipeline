pipeline {
    agent any
    /*environment {
    //NEXUS_CREDS = credentials('nexus-credentials-id')
    } */
    stages {
       /*stage('Containers run') {
            steps {
              sh 'docker compose up -d'
              }  
            }
        }*/
        stage('sonarqube scan') {
            tools {
              sonarQube 'SonarQube'
            }
            steps {
              withSonarQubeEnv('SonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }
        stage('Build') {
            steps {
              sh 'docker build -t nginx .'
            }
        }
        /*stage('Login') {
            steps {
                sh 'docker login -u $NEXUS_CREDS_USR -p $NEXUS_CREDS_PSW localhost:8082'
            }
            }
        stage('Push') {
          steps {
                //withDockerRegistry([ credentialsId: "nexus-credentials-id", url: "http://localhost:8082" ]) {
                sh 'docker tag nginx_test localhost:8082/nginx_test'
                sh 'docker push localhost:8082/nginx_test'   
            //}
          }
    }*/
  }

}
