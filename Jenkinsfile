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
    }
}
