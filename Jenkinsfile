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

            // Run pytest inside container, install dependencies first
            bat 'docker run --rm -v %cd%:/app -w /app python:3.11-slim sh -c "pip install -r requirements.txt && pytest python/maths/tests/test_fibonacci.py"'
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
