pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install -r requirements.txt'
            }
        }

        stage('Django Check') {
            steps {
                sh 'python3 manage.py check'
            }
        }

        stage('Run Django') {
            steps {
                sh 'nohup python3 manage.py runserver 0.0.0.0:8000 > django.log 2>&1 &'
            }
        }
    }
}
