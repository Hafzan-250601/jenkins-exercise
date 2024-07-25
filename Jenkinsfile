pipeline {
    agent any
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                sudo apt-get update
                sudo apt-get upgrade -y
                sudo apt install python3 -y
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'sudo apt update && apt upgrade -y'
                sh 'sudo apt-get install python3 -y'
                sh 'sudo apt-get install python3-venv -y'
                sh 'sudo apt-get install python3-pip -y'
                sh 'python3 -m venv .venv'
                sh '. .venv/bin/activate'
                sh 'pip install datetime --break-system-packages'
                sh 'python3 py_test.py'
            }
        }
        stage('Deliver') {
            steps {
                sh '''
                echo "Ready to deliver"
                '''
            }
        }
    }
}
