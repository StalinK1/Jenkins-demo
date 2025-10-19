pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh './hello.sh > output.txt'
            }
        }
    }

    post {
        success {
            emailext (
                subject: "Jenkins Build Successful - ${env.JOB_NAME}",
                body: "Build completed successfully.\n\nOutput attached.",
                to: "your-email@example.com",
                attachmentsPattern: "output.txt"
            )
        }
        failure {
            emailext (
                subject: "Jenkins Build Failed - ${env.JOB_NAME}",
                body: "Build failed. Check Jenkins logs.",
                to: "your-email@example.com"
            )
        }
    }
}
