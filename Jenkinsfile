pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                sh 'python3 -m pip install --upgrade pip'
                sh 'python3 -m pip install -r requirements.txt'

            }

        }

        stage('Test') {

            steps {

                sh 'python3 -m pytest'

            }

        }

        stage('Deploy') {

            steps {

                echo 'Deploying to Staging...'

            }

        }

    }

}