pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                echo 'Code cloned from GitHub'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                mkdir -p /tmp/calculator
                cp index.html /tmp/calculator/
                '''
            }
        }
    }

    post {
        success {
            echo "Calculator deployed successfully!"
        }
    }
}
