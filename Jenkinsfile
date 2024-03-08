pipeline {
    agent any

    environment {
        // Define the path to Maven executable
        MAVEN_HOME = '/path/to/your/maven' // Update this with the actual path to Maven on your system
        PATH = "$MAVEN_HOME/bin:$PATH" // Add Maven to the system PATH
    }

    stages {
        stage('Build') {
            steps {
                // Maven should be accessible now
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
