pipeline {
    agent any

    stages {
        stage('Install Dependencies with pipx') {
            steps {
                script {
                    // Install dependencies using pipx
                    sh 'pipx install -r requirements.txt'
                }
            }
        }

        // Add other stages as needed
    }
}
