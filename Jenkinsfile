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
       stage('MILSテスト実行') {
            steps {
                // This line will clone the source code repository
                checkout scm
            }
        }

        stage('モデルビルド実行') {
            steps {
                script {
                    // Install Node.js dependencies
                    sh 'npm install'
                    cd /path
                    conmand

                }
            }
        }

        stage('基本動作確認テスト実行') {
            steps {
                script {
                    // Run ESLint for code quality checks
                    sh 'npx eslint .'
                }
            }
        }

        stage('機能確認テスト実行') {
            steps {
                echo 'Pipeline succeeded!'
                // Placeholder for deployment steps
            }
        }

     stage('ReportGeneration') {
            steps {
                echo 'ReportGeneration'
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

