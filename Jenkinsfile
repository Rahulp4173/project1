
pipeline {
    agent any

    tools {
        nodejs 'NodeJS-22'
    }

    options {
        timestamps()
    }

    stages {
        stage('Checkout GitHub') {
            steps {
                checkout scm
            }
        }

        stage('Check Node.js') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Compile JSX') {
            steps {
                sh 'npx babel src/main.js --out-file /tmp/main.js'
                sh 'npx babel src/r1.js --out-file /tmp/r1.js'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: JSX files compiled successfully!'
        }

        failure {
            echo 'FAILED: Check the Console Output.'
        }
    }
}
