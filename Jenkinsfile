pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('Dockerhub')
    }
    stages {
        stage('Checkout') {
            steps {
                git '(https://github.com/30marcel/project-new-pipeline.git)'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t melong123/web-app:1.0.3 .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Dockerhub', passwordVariable: 'DOCKERHUB_PSW', usernameVariable: 'DOCKERHUB_USR')]) {
                    sh 'echo $DOCKERHUB_PSW | docker login -u $DOCKERHUB_USR --password-stdin'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push melong123/web-app:1.0.3'
            }
        }
    }
}
