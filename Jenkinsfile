pipeline {
    agent any

    environment {
        DEPLOY_DIR = "C:\\calculator-app"
        PORT = "8090"
    }

    stages {

        stage('Deploy Files') {
            steps {
                bat '''
                if not exist %DEPLOY_DIR% mkdir %DEPLOY_DIR%
                copy index.html %DEPLOY_DIR%
                '''
            }
        }

        stage('Start Server') {
            steps {
                bat '''
                taskkill /F /IM node.exe >nul 2>&1
                cd %DEPLOY_DIR%
                npx serve . -l %PORT%
                '''
            }
        }
    }

    post {
        success {
            echo "Calculator deployed successfully!"
            echo "Open: http://localhost:8090"
        }
    }
}
