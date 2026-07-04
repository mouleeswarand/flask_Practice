pipeline {

    agent any

    environment {
        MONGO_URI = credentials('mouli-cred')
        SECRET_KEY = credentials('mouli-cred2')
    }

    stages {

        stage('Build') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    . venv/bin/activate
                    pytest
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Staging...'
            }
        }
    }
}