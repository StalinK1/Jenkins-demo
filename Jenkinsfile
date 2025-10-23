pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Always clean workspace first
                deleteDir()
                // Checkout latest code from GitHub
                checkout scm
                // Run your script
                sh 'bash ./hello.sh > output.txt'
            }
        }
    }

    post {
        success {
            emailext (
                subject: "✅ Jenkins Build Successful - ${env.JOB_NAME}",
                body: "Build completed successfully.\n\nOutput file attached.",
                to: "your-email@example.com",
                attachmentsPattern: "output.txt"
            )
        }
        failure {
            emailext (
                subject: "❌ Jenkins Build Failed - ${env.JOB_NAME}",
                body: "Build failed. Please check Jenkins console logs for details.",
                to: "your-email@example.com"
            )
        }
    }
}
