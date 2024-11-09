pipeline {
    agent { 
        node {
            label 'docker-agent-python-alpine'
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
                pip install -r requirements.txt --break-system-packages
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Guney
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
        stage('Email Notification') {
            mail bcc: '', body: 'Hi , from Jekins...', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'guneycancansanli@gmail.com'
        }
    }
}
