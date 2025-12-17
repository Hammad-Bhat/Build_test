pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                 git branch: 'main', url: 'https://github.com/Hammad-Bhat/Build_test.git'
                }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest python/maths/tests/test_fibonacci.py'
            }
        }
    }
}
