pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Use correct branch name
                git branch: 'master', url: 'https://github.com/Heena122/Dummy-project-front-backend-live.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                echo "Installing dependencies..."
                npm install
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                echo "Running tests..."
                npm test
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Starting deployment..."
                npm run build
                cp -r build/* /var/www/html/
                echo "Deployment finished."
                '''
            }
        }
    }
}
