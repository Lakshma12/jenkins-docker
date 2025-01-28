# Automated Process of Docker Image Build and Push To DockerHub with Use Of CI/CD Jenkins
![Image](https://github.com/user-attachments/assets/0ddaa063-0fed-4502-a325-fec39456cb0a)

# Step1 :
1.Jenkins is installed and running,
2.Docker is installed on the Jenkins machine,
3.You have a GitHub repository that contains your application code and a Dockerfile.
4.You have a DockerHub account and a DockerHub repository where the image will be pushed.
5.Jenkins credentials are set up for both GitHub and DockerHub.
# step2:Create a Jenkins Pipeline
Create a Jenkinsfile that defines the pipeline to clone the code, build the Docker image, and push it to DockerHub


# Step3:
Clones the code from GitHub.
Builds a Docker image using the Dockerfile in the repository.
Pushes the Docker image to DockerHub
