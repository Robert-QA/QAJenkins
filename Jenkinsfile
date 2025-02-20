pipeline {
    agent any
    tools {
        maven 'Maven'  // Ensure Maven is installed in Jenkins
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
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'  // Publish JUnit reports
                }
            }
        }
    }
}
