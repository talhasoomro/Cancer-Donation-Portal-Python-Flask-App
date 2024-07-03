pipeline {
    agent any

    environment {
        // Define any environment variables you need
        VENV = "venv"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/talhasoomro/Cancer-Donation-Portal-Python-Flask-App.git'
            }
        }
        
        stage('Setup Python Environment') {
            steps {
                // Install Python and create a virtual environment
                sh 'apt install python3 -y'
                sh 'python3 -m venv $VENV'
                sh './$VENV/bin/pip install --upgrade pip'
            }
        }
}

