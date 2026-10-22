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
                sh '''
                    python3 -m venv .venv
                    .venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Django Check') {
            steps {
                sh '.venv/bin/python manage.py check'
            }
        }

        stage('Run Django') {
            steps {
                sh '''
                    nohup .venv/bin/python manage.py runserver 0.0.0.0:8000 \
                        > django.log 2>&1 &
                '''
            }
        }
    }
}
