pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('nour8776')
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/nourwaled245/Assignment/main'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image from Dockerfile
                    sh 'docker build -t nour90/Assignment .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Log in to Docker Hub and push the image
                    sh '''
                    echo "$DOCKERHUB_CREDENTIALS" | docker login -u <your-dockerhub-username> --password-stdin
                    docker push <your-dockerhub-username>/<project-name>
                    '''
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
