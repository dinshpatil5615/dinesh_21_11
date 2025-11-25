pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-html-app .'
            }
        }

        stage('Stop old container') {
            steps {
                sh '''
                docker rm -f simple-html-container || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d --name simple-html-container -p 8000:80 simple-html-app
                '''
            }
        }
    }
}
