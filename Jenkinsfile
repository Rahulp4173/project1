
pipeline {
    agent any

    tools {
        nodejs 'NodeJS-22'
    }

    options {
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading source code from GitHub'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Build React App') {
            steps {
                bat 'npm run build'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: React application built successfully!'
        }

        failure {
            echo 'FAILED: Check the Console Output for errors.'
        }

        always {
            echo 'Jenkins pipeline finished.'
        }
    }
}
