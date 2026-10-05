pipeline {
    agent any

    stages {

        stage('Start Minikube') {
            steps {
                bat 'minikube start --driver=docker'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'minikube image build student-result:1.0 .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl get deployments'
                bat 'kubectl get pods'
                bat 'kubectl get services'
            }
        }
    }

    post {
        success {
            echo 'Student Result application deployed successfully.'
        }

        failure {
            echo 'Deployment failed. Check the Jenkins console output.'
        }
    }
}