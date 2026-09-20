pipeline {
    agent any

    stages {
        stage('Checkout Test') {
            steps {
                echo 'Jenkinsfile t9ra mzyan'
            }
        }

        stage('Show Files') {
            steps {
                bat 'dir'
                bat 'type app.txt'
            }
        }

        stage('Finish') {
            steps {
                echo 'CI pipeline daz b najah'
            }
        }
    }
}