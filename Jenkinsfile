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
                sh 'apt update'
                sh 'apt install -y python3 python3-venv'
                sh 'python3 -m venv $VENV'
                sh './$VENV/bin/pip install --upgrade pip'
            }
        }
        
        stage('Install Python Dependencies') {
            steps {
                // Install Python dependencies from requirements.txt
                sh './$VENV/bin/pip install -r requirements.txt'
            }
        }
        
        stage('Run Tests') {
            steps {
                // Example: Run your unit tests or other checks
                sh './$VENV/bin/python3 -m pytest'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build Docker image based on Dockerfile
                sh 'docker build -t cancer-donation-app .'
            }
        }
        
        stage('Run Docker Container') {
            steps {
                // Run Docker container using docker-compose
                sh 'docker-compose up -d'
            }
        }
        
        stage('Deploy') {
            steps {
                // Example: Deploy to production or staging environment
                echo 'Deploying...'
                // Add your deployment steps here
            }
        }
    }
}
