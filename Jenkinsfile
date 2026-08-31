pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Soumya11-cloud/jenkins-cicd'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-cicd-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker images my-cicd-app'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker stop my-cicd-app || true
                    docker rm my-cicd-app || true

                    docker run -d \
                    --name my-cicd-app \
                    -p 80:80 \
                    my-cicd-app
                '''
            }
        }
    }
}