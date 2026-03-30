pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Docker Compose Up') {
            steps {
                sh 'docker-compose up -d --build'
            }
        }
        stage('Test Connection') {
            steps {
                sh 'docker ps'
                sh 'curl http://localhost:8081 || true'
            }
        }
    }
    post {
        always {
            sh 'docker-compose down'
        }
    }
}
