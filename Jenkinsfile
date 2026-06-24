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
                echo 'Validating docker-compose.yml'
                sh 'docker-compose config'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker images'
                sh 'docker-compose build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application containers'
                sh '''
                    docker-compose down || true
                    docker-compose up -d
                '''
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying deployment'
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

        always {
            echo 'Pipeline Execution Completed'
        }
    }
}
