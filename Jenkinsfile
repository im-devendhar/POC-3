pipeline {
    agent any

    environment {
        IMAGE_NAME = "frontend-app"
        CONTAINER_NAME = "frontend-container"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/im-devendhar/POC-3.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                if [ "$(docker ps -q -f name=$CONTAINER_NAME)" ]; then
                    docker stop $CONTAINER_NAME
                    docker rm $CONTAINER_NAME
                fi
                '''
                sh 'docker run -d -p 80:80 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
