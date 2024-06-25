pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your code
                checkout scm
            }
        }
        stage('Install dependencies') {
            steps {
                // Example for a Node.js project
                sh 'npm install'
            }
        }
        stage('Snyk Scan') {
            steps {
                withCredentials([string(credentialsId: 'snyk-token', variable: 'SNYK_TOKEN')]) {
                    sh 'npx snyk test --all-projects --severity-threshold=high'
                }
            }
        }
    }

    post {
        always {
            // Archive scan results or take necessary actions
        }
    }
}
