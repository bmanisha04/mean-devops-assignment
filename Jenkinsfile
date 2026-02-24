pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'dockerhub-creds'
        IMAGE_BACKEND = 'manisha417/mean-backend'
        IMAGE_FRONTEND = 'manisha417/mean-frontend'
        VM_IP = '20.193.144.86'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/bmanisha04/mean-devops-assignment.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker build -t $IMAGE_BACKEND:latest ./backend'
                sh 'docker build -t $IMAGE_FRONTEND:latest ./frontend'
            }
        }

        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push $IMAGE_BACKEND:latest'
                    sh 'docker push $IMAGE_FRONTEND:latest'
                }
            }
        }

        stage('Deploy to Azure VM') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'azure-vm-ssh',
                    usernameVariable: 'VM_USER',
                    passwordVariable: 'VM_PASS'
                )]) {
                    sh """
                    sshpass -p $VM_PASS ssh -o StrictHostKeyChecking=no $VM_USER@$VM_IP '
                        cd mean-app &&
                        docker-compose pull &&
                        docker-compose down &&
                        docker-compose up -d
                    '
                    """
                }
            }
        }
    }
}