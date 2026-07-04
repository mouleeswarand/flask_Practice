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
                    pwd
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    . venv/bin/activate

                    echo "Checking MONGO_URI..."

                    if [ -z "$MONGO_URI" ]; then
                        echo "MONGO_URI is EMPTY"
                    else
                        echo "MONGO_URI exists"
                        echo "$MONGO_URI" | cut -c1-30
                    fi

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

    post {
        success {
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build completed successfully.",
                to: "dmouleeswaran@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build has failed. Please check the console output.",
                to: "dmouleeswaran@gmail.com"
            )
        }
    }
}