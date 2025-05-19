pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t toladoc/jenkins-docker-app .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
                sh 'docker push toladoc/jenkins-docker-app'
            }
        }
    }
}
