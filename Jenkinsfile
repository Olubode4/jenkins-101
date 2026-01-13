pipeline {
    agent {
        node {
            label 'docker-agent-python-2'
            }
    }

    triggers {
        // maybe slow this down too; every minute is pretty aggressive
        pollSCM('H/5 * * * *')  // every 5 minutes, for example
    }

    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                    set -e
                    cd myapp

                    # NO venv creation, NO pip install here
                    # deps already installed into /opt/venv and PATH points to it

                    python -m compileall .
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                    set -e
                    cd myapp

                    python hello.py
                    python hello.py --name=Brad
                '''
            }
        }

        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                    echo "doing delivery stuff.."
                '''
            }
        }
    }
}
