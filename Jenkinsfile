pipeline {
    agent any

    environment {
        // Default input for Fibonacci script
        FIB_INPUT = "%FIB_INPUT%"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        
        stage('Set up Python Container') {
            steps {
                script {
                    // Pull Python image (if not already present)
                    bat 'docker pull python:3.11-slim'
                    
                    // Check Python version inside container
                    bat 'docker run --rm python:3.11-slim python --version'
                    bat 'docker run --rm python:3.11-slim pip --version'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Run pip install inside container, mounting workspace
                    bat 'docker run --rm -v %cd%:/app -w /app python:3.11-slim pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run pytest inside container
                    bat 'docker run --rm -v %cd%:/app -w /app python:3.11-slim pytest python\\maths\\tests\\test_fibonacci.py'
                }
            }
        }

        stage('Run Fibonacci') {
            steps {
                script {
                    // Run your Fibonacci script inside container
                    bat 'docker run --rm -v %cd%:/app -w /app python:3.11-slim python python\\maths\\fibonacci.py %FIB_INPUT%'
                }
            }
        }
    }
}
