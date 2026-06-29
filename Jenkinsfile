pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t aishu-website:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat '''
                docker stop aishu-container || exit 0
                docker rm aishu-container || exit 0
                docker run -d --name aishu-container -p 9090:80 aishu-website:v1
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'docker ps'
            }
        }
    }
}