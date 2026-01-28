pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "karthikarajendran19/trend-data"
        AWS_REGION = "ap-south-1"        // replace with your region
        EKS_CLUSTER = "trend-data-eks-cluster"    // replace with your EKS cluster name
    }

    stages {    
        stage('Build Image') {
            steps { 
                sh 'docker build -t $DOCKER_IMAGE:latest .' 
            }
        }

        stage('Push Image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    sh 'docker push $DOCKER_IMAGE:latest'
                }
            }
        }

        stage('Deploy to EKS') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'aws-eks-credentials'   // your AWS IAM credentials in Jenkins
                ]]) {
                    sh '''
                        # Configure kubectl with AWS EKS
                        aws eks update-kubeconfig --name $EKS_CLUSTER --region $AWS_REGION

                        # Deploy to EKS
                        kubectl apply -f deployment.yaml
                        kubectl apply -f service.yaml
                    '''
                }
            }
        }
    }
}
