pipeline {
    agent any  // use any available Jenkins agent

    stages {
        stage('Checkout Code') {
            steps {
                // Clone your GitHub repository
                git branch: 'main', url: 'https://github.com/Hammad-Bhat/Build_test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Python dependencies from requirements.txt
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Run your pytest tests
                bat 'pytest python/maths/tests/test_fibonacci.py'
            }
        }
    }
}
// trying