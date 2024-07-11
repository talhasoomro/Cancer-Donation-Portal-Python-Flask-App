pipeline {
    agent any

    environment {
        // Define the deployment directory
        DEPLOY_DIR = '/home/pyprodep'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub repository
                git 'https://github.com/talhasoomro/Cancer-Donation-Portal-Python-Flask-App.git'
            }
        }
        
        stage('Build') {
            steps {
                // Install dependencies and build the Flask application
                sh 'pip install -r requirements.txt'  // Adjust as per your requirements file
                sh 'python manage.py migrate'         // Example manage.py command for migrations
                sh 'python manage.py collectstatic --noinput' // Example for collecting static files
                // Add other build steps as necessary
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application to the specified directory
                sh "cp -r . ${DEPLOY_DIR}"
            }
        }
    }

    // Post-build actions
    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
