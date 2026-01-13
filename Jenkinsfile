pipeline {
    agent {
        docker {
            image 'python:3.11-slim'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                    set -e
                    cd myapp

                    python -m venv .venv
                    . .venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    set -e
                    cd myapp
                    . .venv/bin/activate
                    python hello.py
                    python hello.py --name=Brad
                '''
            }
        }
    }
}
