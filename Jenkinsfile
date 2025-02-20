pipeline {
    agent any
    tools {
        maven 'Maven 3.6.3'  // Ensure Maven is installed in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Robert-QA/QAJenkins'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn --version'
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
