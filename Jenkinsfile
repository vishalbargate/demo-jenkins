pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "🚀 Building ${env.BRANCH_NAME} branch..."
            }
        }
    }

    post {
        success {
            office365ConnectorSend(
                message: "✅ SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER} (${env.BRANCH_NAME})"
            )
        }
        failure {
            office365ConnectorSend(
                message: "❌ FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER} (${env.BRANCH_NAME})"
            )
        }
    }
}
