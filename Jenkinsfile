pipeline {
    agent {
        docker {
            image 'python:3'   // Official image that has Python 3 pre-installed
            args '-u root'     // Run as root to allow pip install
        }
    }

    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python hello.py
                python hello.py --name=Alex
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
