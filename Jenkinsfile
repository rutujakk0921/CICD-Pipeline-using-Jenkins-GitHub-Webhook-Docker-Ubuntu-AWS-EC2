pipeline{
    agent any

    environment{
        CONTAINER_NAME = "nestjs-app"
        IMAGE_NAME = "nestjs-image"
        EMAIL = "rutukadam921@gmail.com"
        PORT = "3000"
    }

    stages{
        stage('clone repo'){
         steps{
            git branch: 'main', url:'https://github.com/rutujakk0921/CICD-Pipeline-using-Jenkins-GitHub-Webhook-Docker-Ubuntu-AWS-EC2.git'
            }
         }

         stage('Build Docker Image'){
            steps{
                sh 'docker build -t $IMAGE_NAME'
            }
         }
         stage('Stop & Remove Previous Container'){
            steps{
                sh '''
                    docker stop $CONTAINER_NAME ||
                    true
                    docker rm $CONTAINER_NAME || true
                '''
            }
         }
         stage('Docker Container Run'){
            steps{
                sh '''
                    docker run -d -p ${port}:${PORT}
                    --name $CONTAINER_NAME
                '''
            }
         }
    }
}