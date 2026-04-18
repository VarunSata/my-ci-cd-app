pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                python3 -m venv venv
                venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                venv/bin/python test_app.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                pkill -f "python3 app.py" || true
                nohup python3 app.py > app.log 2>&1 &
                '''
            }
        }
    }
}