pipeline {
    agent any
    environment{
      DOCKERHUB_CREDENTIALS = credentials('Dockerhub')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t 30marcel/web-app:1.0.3 .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push 30marcel/web-app:1.0.3'
            }
        }
        stage('Logout') {
            steps {
                sh 'docker logout'
            }
        }
    }
}
