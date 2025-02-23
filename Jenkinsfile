pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/Anushma/pet-clinic.git'
            }
        }
        stage('Build') {
            steps {
                // Build the Spring Boot application using Maven
                bat 'mvn clean package'
            }
        }
        stage('Check Files') {
            steps {
                // Verify the presence of application.properties
                bat 'dir src\\main\\resources\\application.properties'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                bat 'mvn test'
            }
        }
        stage('Archive Artifacts') {
            steps {
                // Archive the built artifacts
                archiveArtifacts artifacts: 'target\\*.jar', fingerprint: true
            }
        }
    }
    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
