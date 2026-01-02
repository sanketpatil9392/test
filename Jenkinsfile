


pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-web-app:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f my-web-app || true
                docker run -d -p 9094:80 --name my-web-app my-web-app:latest
                '''
            }
        }
    }
}

