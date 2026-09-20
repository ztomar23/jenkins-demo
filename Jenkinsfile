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
                bat '''
                for /L %%i in (1,1,10) do (
                    curl.exe -f http://localhost:8081 && exit /b 0
                    echo Application mazal ma ready... tentative %%i/10
                    powershell -NoProfile -Command "Start-Sleep -Seconds 2"
                )

                echo Application ma jawbatch ba3d 10 tentatives
                docker ps
                docker logs jenkins-demo-container
                exit /b 1
                '''
            }
        }

        stage('Finish') {
            steps {
                echo 'Pipeline Docker daz b najah'
            }
        }
    }
}