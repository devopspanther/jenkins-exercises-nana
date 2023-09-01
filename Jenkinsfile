pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'Dockerhub-cred' // Set this to your Docker Hub credentials ID
        IMAGE_NAME = 'my-node-app'
        IMAGE_TAG = 'latest'
    }

    stages {
        stage('Test') {
            steps {
                script {
                    // Use Node.js and npm to install dependencies and build the app
                    echo 'Testing docker image'
                    sh 'cd app/'
                    sh 'npm install'
                    sh 'npm test'
            }
        }

        stage('Dockerize and Push') {
            steps {
                script {
                    // Build the Docker image
                    docker.build("${IMAGE_NAME}:${IMAGE_TAG}")

                    // Log in to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', DOCKERHUB_CREDENTIALS) {
                        // Push the Docker image to Docker Hub
                        docker.image("${IMAGE_NAME}:${IMAGE_TAG}").push()
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up any temporary files or resources
        }
    }
}
}
