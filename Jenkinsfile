pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                bat 'python -m pip install --upgrade pip'
                bat 'pip install -r requirements.txt'

            }

        }

        stage('Test') {

            steps {

                bat 'pytest'

            }

        }

        stage('Deploy') {

            steps {

                echo 'Deploying to Staging...'

            }

        }

    }

}