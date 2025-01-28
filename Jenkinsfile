pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('123456')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
           git branch: 'main', credentialsId: '123465', url: 'https://github.com/Lakshma12/jenkins-docker.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t reddy557/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push reddy557/nodeapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
