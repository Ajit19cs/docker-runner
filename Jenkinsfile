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
            
            // Archive the entire folder containing the HTML report, its related resources, and the spark folder
            archiveArtifacts allowEmptyArchive: true, artifacts: 'dockerOutput/result/*/index.html, dockerOutput/result/*/spark/**/*', fingerprint: true
        }
    }
}
