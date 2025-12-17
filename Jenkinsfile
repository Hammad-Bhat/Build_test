pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Hammad-Bhat/Build_test.git'
            }
        }

        stage('Hello') {
            steps {
                echo 'Hello, Jenkins is running!'
            }
        }

        stage('List Workspace') {
            steps {
                bat 'dir'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
