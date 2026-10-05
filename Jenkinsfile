pipeline {
    agent any

    stages {

        stage('Test Minikube') {
            steps {
                bat 'whoami'
                bat 'minikube profile list'
                bat 'minikube status'
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