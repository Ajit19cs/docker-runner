pipeline {
    agent any

    stages {
        stage('Run Test') {
            steps {
                // Start containers in detached mode
                bat "docker-compose up -d"
                
                // Wait for the test container to finish execution by monitoring logs
                bat "docker-compose logs -f testframework-container"
            }
        }

        stage('Stop the Docker Image') {
            steps {
                // Stop and remove the containers after the test execution is complete
                bat "docker-compose down"
            }
        }
    }
}
