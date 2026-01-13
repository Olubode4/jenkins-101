pipeline {
    agent {
        node {
            label 'docker-agent-python'   // <-- your CI image
            // args '-u root'  // only if you ever need root inside the container
        }
    }

    triggers {
        pollSCM('H/5 * * * *')  // every 5 minutes is enough; '* * * * *' is heavy
    }

    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                    set -e
                    cd myapp

                    # deps are already baked into the image
                    pip install -r requirements.txt --break-system-packages
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                    set -e
                    cd myapp

                    python3 hello.py
                    python3 hello.py --name=Brad
                '''
            }
        }

        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh 'echo "doing delivery stuff.."'
            }
        }
    }
}
