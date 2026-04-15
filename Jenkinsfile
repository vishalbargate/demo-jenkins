pipeline {
    agent any

    stages {
        stage('Build Java') {
            steps {
                sh 'javac src/main/java/App.java'
            }
        }

        stage('Run App') {
            steps {
                sh 'java -cp src/main/java App'
            }
        }

        stage('Environment Based Action') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'dev') {
                        echo "Deploying to DEV environment"
                    } else if (env.BRANCH_NAME == 'uat') {
                        echo "Deploying to UAT environment"
                    } else if (env.BRANCH_NAME == 'prod') {
                        echo "Deploying to PROD environment"
                    } else {
                        echo "Other branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }
    }
}
