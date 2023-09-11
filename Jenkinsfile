pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Define the Docker image name and tag
                    def dockerImage = "your-docker-registry/your-web-app:${BUILD_NUMBER}"

                    // Build the Docker image
                    bat "docker build -t ${dockerImage} ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Define the Docker image name and tag
                    def dockerImage = "your-docker-registry/your-web-app:${BUILD_NUMBER}"

                    // Log in to Docker registry (if needed)
                    // bat "docker login -u your-username -p your-password"

                    // Push the Docker image to the registry
                    bat "docker push ${dockerImage}"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Define the Docker image name and tag
                    def dockerImage = "your-docker-registry/your-web-app:${BUILD_NUMBER}"

                    // SSH into your server and run the Docker container
                    // Replace 'user' and 'your-server-address' with your server details
                    bat """
                        ssh user@your-server-address "docker pull ${dockerImage}"
                        ssh user@your-server-address "docker run -d -p 80:80 ${dockerImage}"
                    """
                }
            }
        }
    }
}
