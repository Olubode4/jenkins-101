pipeline {
    agent {
        node {
            label 'docker-agent-python-2'
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
