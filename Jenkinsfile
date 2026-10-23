
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
                sh 'test -f index.html'
                echo 'HTML file exists - Test passed.'
            }
        }

        stage('Build') {
            steps {
                sh 'mkdir -p build'
                sh 'cp index.html build/index.html'
                echo 'HTML application built successfully.'
            }
        }

        stage('Verification') {
            steps {
                sh 'test -f build/index.html'
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
