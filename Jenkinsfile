pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
    }

    post {
        success {
            office365ConnectorSend(
                webhookUrl: 'PASTE_YOUR_WEBHOOK_URL',
                message: "✅ SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
        failure {
            office365ConnectorSend(
                webhookUrl: 'PASTE_YOUR_WEBHOOK_URL',
                message: "❌ FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
    }
}
