pipeline {
    agent any

    environment {
        DOCKERHUB_REPO = 'radha96/trend-app'
        IMAGE_TAG = 'latest'
        AWS_REGION = 'ap-south-1'
        EKS_CLUSTER = 'trend-cluster'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Radha96dev/Trend.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKERHUB_REPO:$IMAGE_TAG .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push $DOCKERHUB_REPO:$IMAGE_TAG'
                }
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh 'aws eks update-kubeconfig --region $AWS_REGION --name $EKS_CLUSTER'
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
                sh 'kubectl rollout restart deployment trend-app'
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
