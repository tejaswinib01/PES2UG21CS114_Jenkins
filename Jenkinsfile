pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install' // Build the Maven project
                echo 'Build Stage Successful'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' // Run tests for the Maven project
                echo 'Test Stage Successful'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' // Publish JUnit test results
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn deploy' // Deploy the Maven project
                echo 'Deployment Successful'
            }
        }
    }
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
