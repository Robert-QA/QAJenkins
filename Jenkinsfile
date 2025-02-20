pipeline {
    agent any
    tools{
        maven 'Maven 3.8.4' // Ensure Maven is installed on Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Robert-QA/QAJenkins.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
                echo "Building the project..."
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo "Running tests..."
            }
            post {
                always {
                    junit '**/target/surefire-reports.*.xml' // Publish Reports
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying application..."
            }
        }
    }
}