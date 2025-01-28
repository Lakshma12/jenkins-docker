# Automated Process of Docker Image Build and Push To DockerHub with Use Of CI/CD Jenkins
![Image](https://github.com/user-attachments/assets/0ddaa063-0fed-4502-a325-fec39456cb0a)

# Step1 :
1.Jenkins is installed and running.
2.Docker is installed on the Jenkins machine.
3.You have a GitHub repository that contains your application code and a Dockerfile.
4.You have a DockerHub account and a DockerHub repository where the image will be pushed.
5.Jenkins credentials are set up for both GitHub and DockerHub.
# step2:Create a Jenkins Pipeline
Create a Jenkinsfile that defines the pipeline to clone the code, build the Docker image, and push it to DockerHub
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

# Step3:
Clones the code from GitHub.
Builds a Docker image using the Dockerfile in the repository.
Pushes the Docker image to DockerHub
