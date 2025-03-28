pipeline {
    agent any

    environment {
        PYTHONIOENCODING = 'utf-8'  // Ép Python sử dụng UTF-8
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/TranTheBao12/test_t5.git'
            }
        }

        stage('Set Up Environment') {
            steps {
                script {
                    bat '''
                    if not exist venv (
                        C:\\Users\\USER\\AppData\\Local\\Programs\\Python\\Python312\\python -m venv venv
                    )
                    venv\\Scripts\\python -m pip install --upgrade pip
                    venv\\Scripts\\python -m pip install -r requirements.txt
                    '''
                }
            }
        }

        stage('Start Flask Server') {
            steps {
                script {
                    bat """
        venv\\Scripts\\python app.py > flask_output.log 2>&1 &
        ping -n 6 127.0.0.1 > nul
        """
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    bat '''
                    venv\\Scripts\\python test_todolist.py
                    '''
                }
            }
        }
    }
}
