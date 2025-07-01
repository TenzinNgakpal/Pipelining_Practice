pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'myapp'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git credentialsId: 'github-creds', url: 'git@github.com:your-user/your-repo.git', branch: 'main'
            }
        }

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
