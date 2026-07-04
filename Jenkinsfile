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
}