pipeline {
    agent any

   
    stages {
        stage('run test ') {
            steps {
                bat "docker-compose up -d"
            }
        }

        
        stage('stop the docker image') {
            steps {
                bat "docker-compose down"
            }
        }

        
    }
}
