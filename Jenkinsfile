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
        
        stage('Set up Python Container and Run Tests') {
            steps {
                script {
                    // Pull Python image (if not already present)
                    bat 'docker pull python:3.11-slim'

                    // Check Python and pip inside container (optional)
                    bat 'docker run --rm python:3.11-slim python --version'
                    bat 'docker run --rm python:3.11-slim pip --version'

                    // Install dependencies and run pytest in one command
                    bat 'docker run --rm -v %cd%:/app -w /app python:3.11-slim sh -c "pip install -r requirements.txt && pytest python\\\\maths\\\\tests\\\\test_fibonacci.py"'
                }
            }
        }

        stage('Run Fibonacci') {
            steps {
                script {
                    // Run your Fibonacci script inside container
                    bat 'docker run --rm -v %cd%:/app -w /app python:3.11-slim python python\\\\maths\\\\fibonacci.py %FIB_INPUT%'
                }
            }
        }
    }
}
