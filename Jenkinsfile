pipeline {
    agent any

     environment {
        FIB_INPUT = credentials('99')  // secret ID
    }


    stages {

        // When checkout scm is needed

        // Check out multiple repos

        // stage('Checkout Code') {
        //     steps {
        //         checkout scm
        //     }
        // }

        stage('Pull Python Image') {
            steps {
                bat 'docker pull python:3.11-slim'
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                docker run --rm ^
                -v "%WORKSPACE%:/app" ^
                -w /app ^
                 python:3.11-slim ^
                 sh -c "pip install pytest && python -m pytest python/maths/tests/test_fibonacci.py"
                 '''
    }
}


        stage('Run Fibonacci') {
            steps {
                bat '''
                docker run --rm ^
                -v "%WORKSPACE%:/app" ^
                -w /app ^
                python:3.11-slim ^
                python python/maths/fibonacci.py %FIB_INPUT%
                '''
            }
        }
    }
}
