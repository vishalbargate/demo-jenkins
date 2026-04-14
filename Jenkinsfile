pipeline {
    agent any

    stages {
        stage('GitHub Build') {
            steps {
                echo 'Triggered from GitHub!'
            }
        }
    }
}
post {
    success {
        emailext (
            to: 'vishalbargate@gmail.com',
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Build succeeded!"
        )
    }
    failure {
        emailext (
            to: 'vishalbargate@gmail.com',
            subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Build failed!"
        )
    }
}
