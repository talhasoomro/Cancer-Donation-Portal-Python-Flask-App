pipeline {
    agent any

    stages {
        stage('Python Version') {
            steps {
                sh "sudo apt update"
                sh "sudo apt install python3-venv -y"
                sh "python3 --version"
            }
        }

        stage('Checkout') {
            steps {
                // Checkout your repository from GitHub
                git 'https://github.com/yourusername/your-repo.git'
            }
        }

        stage('Build and Test') {
            steps {
                // Set up Python virtual environment
                sh "python3 -m venv venv"
                sh "source venv/bin/activate"
                
                // Install dependencies and run tests
                sh "pip install -r requirements.txt"
                sh "pytest"
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your application
                sh "docker-compose -f docker-compose.prod.yml build"
                sh "docker-compose -f docker-compose.prod.yml up -d"
            }
        }
    }

    post {
        success {
            echo "Pipeline succeeded! Application deployed."
        }
        failure {
            echo "Pipeline failed. Deployment aborted."
        }
    }
}
