pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull latest code from GitHub
                git branch: 'main', url: 'https://github.com/Heena122/Dummy-project-front-backend-live.git'
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
                # Example deployment commands:
                # Build frontend
                npm run build

                # Copy build artifacts to server directory
                cp -r build/* /var/www/html/

                echo "Deployment finished."
                '''
            }
        }
    }
}
