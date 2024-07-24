pipeline {
    agent any
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                apt-get update
                apt-get upgrade -y
                apt install python3 -y
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'apt update && apt upgrade -y'
                sh 'apt-get install python3 -y'
                sh 'apt-get install python3-venv -y'
                sh 'apt-get install python3-pip -y'
                sh 'python3 -m venv .venv'
                sh '. .venv/bin/activate'
                sh 'pip install datetime'
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