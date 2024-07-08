pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/talhasoomro/Cancer-Donation-Portal-Python-Flask-App'
            }
        }

        stage('Deploy') {
            steps {
                sh "pip install -r requirements.txt"
                sh "app.py"
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

