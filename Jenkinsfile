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
        python3 -m venv .venv
        . .venv/bin/activate
        pip install --upgrade pip
        pip install -r requirements.txt || echo "No requirements.txt found"
        '''
    }
}

stage('Run Tests') {
    steps {
        sh '''
        . .venv/bin/activate
        echo "Running Django tests..."
        python manage.py test
        '''
    }
}

stage('Deploy') {
    steps {
        sh '''
        . .venv/bin/activate
        echo "Applying migrations and collecting static files..."
        python manage.py migrate
        python manage.py collectstatic --noinput
        '''
    }
}

    }
}
