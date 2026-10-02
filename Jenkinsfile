pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sreeja1628/jenkins-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t jenkins-cicd-app:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running application test...'
                sh 'docker run --rm jenkins-cicd-app:latest node --check app.js'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh '''
                    docker stop jenkins-cicd-container || true
                    docker rm jenkins-cicd-container || true
                    docker run -d \
                      --name jenkins-cicd-container \
                      -p 3000:3000 \
                      jenkins-cicd-app:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}
