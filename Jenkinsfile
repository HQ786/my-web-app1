pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my-web-app-image'
        GIT_REPO_URL = 'https://github.com/HQ786/my-web-app1.git'  // Replace with your GitHub repo URL
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: "${GIT_REPO_URL}"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container to verify that it works
                    docker.image("${DOCKER_IMAGE}").run('-p 5000:5000')
                }
            }
        }
    }
}
