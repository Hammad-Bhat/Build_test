pipeline {
    agent any

    environment {
        FIB_INPUT = credentials('99')   // Secret Text credential
    }

    stages {

        stage('Verify Python') {
            steps {
                bat '''
                python --version
                pip --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                pip install --upgrade pip
                pip install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                python -m pytest python/maths/tests/test_fibonacci.py
                '''
            }
        }

        stage('Run Fibonacci') {
            steps {
                bat '''
                python python/maths/fibonacci.py %FIB_INPUT%
                '''
            }
        }
    }
}
