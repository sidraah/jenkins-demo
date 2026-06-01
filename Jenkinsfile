pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sidraah/jenkins-demo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'docker build -t jenkins-demo .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run --rm jenkins-demo'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                docker stop jenkins-demo-container || exit 0
                docker rm jenkins-demo-container || exit 0
                docker run -d --name jenkins-demo-container jenkins-demo
                '''
            }
        }
    }
}