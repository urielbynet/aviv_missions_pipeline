pipeline {
    agent any 
    stages {
        stage('Test') {
            steps {
                docker.build("my-image-name")
            }
        }
    }
}
