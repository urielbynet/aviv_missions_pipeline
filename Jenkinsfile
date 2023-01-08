pipeline {
    
    agent any
    
    environment {
        imageName = "nginx"
        registryCredentials = "nexus_cred"
        registry = "http://localhost:8082/#browse/browse"
        dockerImage = ''
         
    }
    
    stages {
        stage('Code checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/nadavmarkuss/Bynet-Final-Project']])
        }
            
        }
        
         // Building Docker images
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imageName
        }
      }
    }