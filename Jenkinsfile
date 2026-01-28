pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "karthikarajendran19/trend-data"
    }

   
       stage('Build Image') {
            steps { 
                sh 'docker build -t $DOCKER_IMAGE:latest .' 
            }
        }

        stage('Push Image') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-credentials', url: '']) {
                    sh 'docker push $DOCKER_IMAGE:latest'
                }
            }
        }

        stage('Deploy to EKS') {
            steps {
                // Make sure kubectl is configured and kubeconfig is set
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}

