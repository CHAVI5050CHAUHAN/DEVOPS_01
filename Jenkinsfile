pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Pulling latest code from GitHub'
                checkout scm
            }
        }

        stage('Validate') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Application Deployment Completed'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful'
        }
        failure {
            echo 'Deployment Failed'
        }
    }
}
