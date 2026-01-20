pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-calculator-app"
        CONTAINER_NAME = "my-calculator-container"
        PORT = "8090"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Using code from GitHub"
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat '''
                docker stop %CONTAINER_NAME% >nul 2>&1 || exit 0
                docker rm %CONTAINER_NAME% >nul 2>&1 || exit 0
                '''
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p %PORT%:80 --name %CONTAINER_NAME% %IMAGE_NAME%'
            }
        }
    }

    post {
        success {
            echo "Docker CI/CD Pipeline Successful!"
            echo "Open: http://localhost:8090"
        }
    }
}
