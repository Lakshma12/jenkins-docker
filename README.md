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
 (```stage('Build Docker Image') {
    steps {
        script {
            // Build Docker image with dynamic tag using Jenkins build number
            sh 'docker build -t reddy557/nodeapp:${BUILD_NUMBER} .'
        }
    }
}

stage('Login to DockerHub') {
    steps {
        script {
            // Login to DockerHub using Jenkins credentials (ensure credentials are configured in Jenkins)
            docker.withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
            }
        }
    }
}

stage('Push Image to DockerHub') {
    steps {
        script {
            // Push Docker image to DockerHub with the tag as the build number
            sh 'docker push reddy557/nodeapp:${BUILD_NUMBER}'
        }
    }
}
 )
