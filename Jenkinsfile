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

                bat 'mvn clean package'  // Builds the Spring Boot application

                // git 'http://github.com/USER/REPO.git'
                // Run Maven Wrapper Commands
                echo 'Building the Project with maven compile'

            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'  // Runs unit tests
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run Application') {
            steps {
               bat 'java -jar target/pet-clinic-1.0.0.jar''  // Executes the generated JAR file
            }
        }
    }
}
