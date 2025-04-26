pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'docker build -t my-app:latest .'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'python -m pytest'  
            }
        }
        stage('Deploy to Test') {
            steps {
                echo 'Deploying to test environment...'
                sh 'kubectl apply -f k8s/test-deployment.yaml'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                sh 'kubectl apply -f k8s/prod-deployment.yaml'
            }
        }
    }
}
