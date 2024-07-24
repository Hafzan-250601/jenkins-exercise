pipeline {
    agent any
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                apt update
                apt upgrade -y
                apt-get install python3.10 -y
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'apt-get update && apt-get upgrade -y'
                sh 'apt install python3.10 -y'
                sh 'apt install python3-venv -y'
                sh 'apt install python3-pip -y'
                sh 'python3 -m venv .venv'
                sh '. .venv/bin/activate'
                sh 'pip3 install DateTime'
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