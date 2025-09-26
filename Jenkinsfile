pipeline {
    agent any
    environment {
        IMAGE_BACKEND = "fullstack-backend:latest"
        IMAGE_FRONTEND = "fullstack-frontend:latest"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/irphan7982/fullstack-app.git'
            }
        }

        stage('Build Backend') {
            steps {
                echo 'Building Backend Docker image...'
                sh 'docker build -t $IMAGE_BACKEND -f Dockerfile.backend .'
            }
        }

        stage('Build Frontend') {
            steps {
                echo 'Building Frontend Docker image...'
                sh 'docker build -t $IMAGE_FRONTEND -f Dockerfile.frontend .'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'echo "Simulating backend tests..."'
                sh 'echo "Simulating frontend tests..."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying using docker-compose...'
                sh 'docker-compose up -d --build'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline Succeeded!'
        }
        failure {
            echo 'CI/CD Pipeline Failed!'
        }
    }
}

