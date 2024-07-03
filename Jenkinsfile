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
                sh 'python3 -m venv $VENV'
                sh './$VENV/bin/pip install --upgrade pip'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install required Python packages
                sh './$VENV/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Run any tests defined for the project
                sh './$VENV/bin/python -m unittest discover'
            }
        }

        stage('Build') {
            steps {
                // Any build steps (e.g., compiling assets)
                echo 'Building the application...'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application
                echo 'Deploying the application...'
            }
        }
    }

    post {
        always {
            // Cleanup steps, such as deleting temporary files
            deleteDir()
        }
    }
}

