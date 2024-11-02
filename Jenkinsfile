pipeline {
    agent any
    environment {
        VENV_DIR = 'venv'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-username/your-python-app.git', branch: 'main', credentialsId: 'git-credentials'
            }
        }
        stage('Setup Python Environment') {
            steps {
                sh '''
                    python3 -m venv ${VENV_DIR}
                    source ${VENV_DIR}/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                    source ${VENV_DIR}/bin/activate
                    pytest
                '''
            }
        }
        stage('Build') {
            steps {
                // Include build steps if applicable
            }
        }
        stage('Deploy') {
            steps {
                // Include deployment steps if applicable
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
