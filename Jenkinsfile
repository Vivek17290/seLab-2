pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building the Flask application..."
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'pip install --upgrade pip'
                    sh 'pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh 'pytest test_app.py'
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
