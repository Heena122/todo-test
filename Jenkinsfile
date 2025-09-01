pipeline {
    agent any

    environment {
        VENV_DIR = '.venv'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Heena122/todo-test.git'
            }
        }

        stage('Set up Python Env') {
            steps {
                sh '''
                echo "Creating virtual environment..."
                python3 -m venv $VENV_DIR
                source $VENV_DIR/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt || echo "No requirements.txt found"
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                source $VENV_DIR/bin/activate
                echo "Running Django tests..."
                python manage.py test
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Simulating deployment... (e.g., collectstatic, migrate)"
                source $VENV_DIR/bin/activate
                python manage.py migrate
                python manage.py collectstatic --noinput
                '''
            }
        }
    }
}
