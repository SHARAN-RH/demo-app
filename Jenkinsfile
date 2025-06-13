pipeline {
    agent any

    environment {
        // Define your image name and local registry
        IMAGE_NAME = "localhost:5000/demo-app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                // This step only applies if you're NOT using "Pipeline script from SCM"
                git 'https://github.com/your-username/demo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh "docker build -t ${IMAGE_NAME} ."
                }
            }
        }

        stage('Push to Local Registry') {
            steps {
                script {
                    // Push the image to local Docker registry
                    sh "docker push ${IMAGE_NAME}"
                }
            }
        }
    }

    post {
        success {
            echo "Docker image ${IMAGE_NAME} pushed successfully!"
        }
        failure {
            echo "Build failed. Check logs above."
        }
    }
}
