pipeline {
    agent {
        docker {
            image 'docker:24.0.2-dind'  // Full Alpine + Docker daemon image
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    environment {
        COMPOSE_PROJECT_NAME = 'myapp'
    }

    stages {
        stage('Install Compose') {
            steps {
                sh 'apk add --no-cache docker-compose'
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
            sh 'docker ps || true'
        }
    }
}
