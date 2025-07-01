pipeline {
    agent {
        docker {
            image 'docker:24.0.2-cli'  // lightweight official Docker CLI image
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    environment {
        COMPOSE_PROJECT_NAME = 'myapp'
    }

    stages {
        stage('Build and Deploy') {
            steps {
                sh 'apk add --no-cache docker-compose'  // install Compose in alpine container
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
