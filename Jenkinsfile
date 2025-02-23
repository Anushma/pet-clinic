pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Anushma/pet-clinic.git'  // Replace with your Git repository
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Builds the Spring Boot application
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'  // Runs unit tests
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar target/*.jar'  // Executes the generated JAR file
            }
        }
    }
}
