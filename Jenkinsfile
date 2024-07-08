pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/talhasoomro/Cancer-Donation-Portal-Python-Flask-App'
            }
        }

        stage('Build and Test') {
            steps {
                sh "pip install -r requirements.txt"
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
