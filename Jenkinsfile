pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/vinudevops/nodejs.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Install Node.js dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run ESLint for code quality checks
                    sh 'npx eslint .'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Pipeline succeeded!'
                // Placeholder for deployment steps
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

