pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building the Docker image...'
                    sh 'docker build -t cicd:latest .'
                }
            }
        }
        stage('Stop and Remove Old Container') {
            steps {
                script {
                    echo 'Stopping and removing old container if it exists...'
                    sh 'docker rm -f cicd-app-container || true'
                }
            }
        }
        stage('Run New Container') {
            steps {
                script {
                    echo 'Running new container...'
                    sh 'docker run -d --name cicd-app-container -p 8001:8001 cicd:latest'
                }
            }
        }
    }
}
