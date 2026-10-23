
pipeline {
    agent any

    tools {
        nodejs 'NodeJS-22'
    }

    options {
        timestamps()
    }

    stages {
        stage('Checkout from GitHub') {
            steps {
                echo 'Downloading source code from GitHub'
                checkout scm
            }
        }

        stage('Check Node.js and npm') {
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

        stage('Check JavaScript Files') {
            steps {
                sh 'node --check src/main.js'
                sh 'node --check src/r1.js'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Node.js checks completed!'
        }

        failure {
            echo 'FAILED: Check the Console Output.'
        }

        always {
            echo 'Jenkins pipeline finished.'
        }
    }
}
