pipeline {
agent any

stages {
    stage('Build') {
        steps {
            echo '🚀 Building DEV branch...'
        }
    }

stage('Deploy to Kubernetes') {
steps {
sh '''
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.27.0/bin/linux/amd64/kubectl
chmod +x kubectl

    ./kubectl apply -f https://raw.githubusercontent.com/vishalbargate/demo-jenkins/dev/demo-app.yaml -n jenkins-cancap
    ./kubectl apply -f https://raw.githubusercontent.com/vishalbargate/demo-jenkins/dev/demo-app-service.yaml -n jenkins-cancap
    '''
}

}
}

    post {
        success {
            script {
                office365ConnectorSend(
                    webhookUrl: 'https://jamesjtonedm.webhook.office.com/webhookb2/bacc618f-4ebe-404b-a1fe-9914f6693678@b80c6ecc-f345-43be-91a2-b28d8d266f2f/IncomingWebhook/a095e82eb889464e9df140afbe5affea/7030b531-431a-4b33-b0dd-6b39be2ba4ee/V2e0M2BzpECDR2tl8ZQp6f6rwcex_Ee7KHjwJtcRkKdZ41',
                    message: " SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER} (DEV)"
                )
            }
        }

        failure {
            script {
                office365ConnectorSend(
                    webhookUrl: 'https://jamesjtonedm.webhook.office.com/webhookb2/bacc618f-4ebe-404b-a1fe-9914f6693678@b80c6ecc-f345-43be-91a2-b28d8d266f2f/IncomingWebhook/a095e82eb889464e9df140afbe5affea/7030b531-431a-4b33-b0dd-6b39be2ba4ee/V2e0M2BzpECDR2tl8ZQp6f6rwcex_Ee7KHjwJtcRkKdZ41',
                    message: " FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER} (DEV)"
                )
            }
        }
    }
}
