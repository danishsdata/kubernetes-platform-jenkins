pipeline {
    agent any
    environment {
        IMAGE = "<REGISTRY>/app:${env.BUILD_NUMBER}"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Test') {
            steps {
                sh 'python -m pytest tests/ -q'
            }
        }
        stage('Build') {
            steps {
                sh "docker build -t ${IMAGE} ."
            }
        }
        stage('Deploy') {
            steps {
                sh "kubectl set image deployment/app app=${IMAGE}"
                sh 'kubectl rollout status deployment/app'
            }
        }
    }
}
