pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }
    }

    post {
        success {
            slackSend(channel: '#ci-cd-notifications', color: 'good', message: 'CI/CD pipeline succeeded!')
        }
        failure {
            slackSend(channel: '#ci-cd-notifications', color: 'danger', message: 'CI/CD pipeline failed!')
        }
    }
}
