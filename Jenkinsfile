pipeline {
    agent any

    environment {
        PYTHONIOENCODING = 'utf-8'  // Ép Python sử dụng UTF-8
    }
stage('Start Flask Server') {
    steps {
        script {
            bat '''
            call venv\\Scripts\\activate
            start /B python app.py
            timeout /T 5
            '''
        }
    }
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
                    call venv\\Scripts\\activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                    '''
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    bat '''
                    call venv\\Scripts\\activate
                    set PYTHONIOENCODING=utf-8
                    python test_todolist.py
                    '''
                }
            }
        }
    }
}
