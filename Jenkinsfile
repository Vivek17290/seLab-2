pipeline {
    agent any

    environment {
        VIRTUAL_ENV = 'venv' 
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Set Up Virtual Environment') {
            steps {
                script {
                    sh 'python -m venv $VIRTUAL_ENV'
                    sh './$VIRTUAL_ENV/bin/pip install --upgrade pip'
                    sh './$VIRTUAL_ENV/bin/pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh './$VIRTUAL_ENV/bin/pytest test_app.py'
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
