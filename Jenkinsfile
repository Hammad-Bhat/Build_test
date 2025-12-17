pipeline {
    agent {
        docker {
            image 'python:3.11-slim'  // Pulls the image directly
        }
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Hammad-Bhat/Build_test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest python/maths/tests/test_fibonacci.py'
            }
        }
    }
}
