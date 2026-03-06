pipeline {

    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:${BUILD_NUMBER} .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop devops-container || true'
                sh 'docker rm devops-container || true'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name devops-container devops-app:${BUILD_NUMBER}'
            }
        }

    }

}
