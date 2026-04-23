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
                webhookUrl: 'https://jamesjtonedm.webhook.office.com/webhookb2/bacc618f-4ebe-404b-a1fe-9914f6693678@b80c6ecc-f345-43be-91a2-b28d8d266f2f/IncomingWebhook/a095e82eb889464e9df140afbe5affea/7030b531-431a-4b33-b0dd-6b39be2ba4ee/V2e0M2BzpECDR2tl8ZQp6f6rwcex_Ee7KHjwJtcRkKdZ41',
                message: " SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER} (${env.BRANCH_NAME})"
            )
        }

        failure {
            office365ConnectorSend(
                webhookUrl: 'https://jamesjtonedm.webhook.office.com/webhookb2/bacc618f-4ebe-404b-a1fe-9914f6693678@b80c6ecc-f345-43be-91a2-b28d8d266f2f/IncomingWebhook/a095e82eb889464e9df140afbe5affea/7030b531-431a-4b33-b0dd-6b39be2ba4ee/V2e0M2BzpECDR2tl8ZQp6f6rwcex_Ee7KHjwJtcRkKdZ41',
                message: " FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER} (${env.BRANCH_NAME})"
            )
        }
    }
}
