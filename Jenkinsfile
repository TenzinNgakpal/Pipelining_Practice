pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'myapp'
    }

    stages {
        stage('Build and Deploy') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        always {
            sh 'docker ps'
        }
    }
}
