pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code tclonea mn GitHub'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t jenkins-demo .'
            }
        }

        stage('Docker Deploy') {
            steps {
                bat 'docker rm -f jenkins-demo-container || exit 0'
                bat 'docker run -d -p 8081:80 --name jenkins-demo-container jenkins-demo'
            }
        }

        stage('Test') {
            steps {
                bat 'curl http://localhost:8081'
            }
        }
    }
}