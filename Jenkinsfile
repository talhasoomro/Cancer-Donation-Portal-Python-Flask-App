pipeline {
    agent {
        docker {
            image 'python:3.9' // Replace with the Python version you need
            args '-u root' // Run as root to install packages if necessary
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/your-repo.git'
            }
        }

        stage('Build and Test') {
            steps {
                sh "python3 -m venv venv"
                sh "source venv/bin/activate && pip install -r requirements.txt"
                sh "pytest"
            }
        }

        stage('Deploy') {
            steps {
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
