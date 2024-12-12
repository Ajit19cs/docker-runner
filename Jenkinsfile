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
    }

    post {
        always {
            // This will run after all stages, regardless of success or failure
            bat "docker-compose down"
            
            // Archive the dynamically created index.html file
            archiveArtifacts allowEmptyArchive: true, artifacts: 'dockerOutput/result/*/index.html', fingerprint: true
        }
    }
}
