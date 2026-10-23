
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Source code retrieved successfully from GitHub.'
            }
        }

        stage('Test') {
            steps {
                bat 'if exist index.html (exit /b 0) else (exit /b 1)'
                echo 'HTML file exists - Test passed.'
            }
        }

        stage('Build') {
            steps {
                bat 'if not exist build mkdir build'
                bat 'copy /Y index.html build\\index.html'
                echo 'HTML application built successfully.'
            }
        }

        stage('Verification') {
            steps {
                bat 'if exist build\\index.html (exit /b 0) else (exit /b 1)'
                echo 'Build verification passed.'
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'CI Pipeline failed. Check the console output.'
        }
    }
}
