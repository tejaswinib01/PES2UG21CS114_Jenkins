pipeline {
    agent {
        docker {
            image 'node:14' // Use Node.js 14 Docker image as the agent
        }
    }
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/tejaswinib01/PES2UG21CS114_Jenkins.git' // Clone the repository
            }
        }
        stage('Install dependencies') {
            steps {
                sh 'npm install' // Install Node.js dependencies
            }
        }
        stage('Build application') {
            steps {
                sh 'npm run build' // Build the Node.js application
            }
        }
        stage('Test application') {
            steps {
                sh 'npm test' // Run tests for the application
            }
        }
        stage('Push Docker image') {
            steps {
                sh 'docker build -t <user>/<image>:$BUILD_NUMBER .' // Build Docker image
                sh 'docker push <user>/<image>:$BUILD_NUMBER' // Push Docker image to repository
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
