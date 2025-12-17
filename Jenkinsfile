pipeline {
    agent any

    // environment {
    //     // Default value like GitHub Actions (vars.FIB_INPUT || 7)
    //     FIB_INPUT = "%FIB_INPUT%"
    // }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        
         stage('Set up Python') {
            steps {
                bat 'python --version'
                bat 'pip --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest python\\maths\\tests\\test_fibonacci.py'
            }
        }

        // stage('Run Fibonacci') {
        //     steps {
        //         bat 'python python\\maths\\fibonacci.py %FIB_INPUT%'
        //     }
        // }
    }
}
