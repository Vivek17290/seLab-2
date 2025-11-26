pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Assuming dependencies are already installed on Jenkins
                    sh 'pytest test.py'  // Run the tests directly without setting up the virtual environment
                }
            }
        }
    }

    post {
        success {
            echo 'Build and tests passed! Sending success notification.'
        }
        failure {
            echo 'Build or tests failed! Sending failure notification.'
        }
    }
}


