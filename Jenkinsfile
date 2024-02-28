pipeline {
    agent {
        kubernetes {
            // Define the pod template for Node.js
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: nodejs-app
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: kubernetes.io/hostname
            operator: In
            values:
            - honda-worker-1

  containers:
  - name: nodejs-container
    image: node:latest
    command:
    - cat
    tty: true
"""
        }
    }

    stages {
       stage('Checkout') {
            steps {
                // This line will clone the source code repository
                checkout scm
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

