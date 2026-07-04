pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                sh 'python -m pip install --upgrade pip'
                sh 'pip install -r requirements.txt'

            }

        }

        stage('Test') {

            steps {

                sh 'pytest'

            }

        }

        stage('Deploy') {

            steps {

                echo 'Deploying to Staging...'

            }

        }

    }

}