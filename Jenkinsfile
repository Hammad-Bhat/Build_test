pipeline {
    agent any

    environment {
        FIB_INPUT = 7
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
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

        stage('Run Fibonacci') {
            steps {
                bat 'python python/maths/fibonacci.py %FIB_INPUT%'
            }
        }
    }
}
