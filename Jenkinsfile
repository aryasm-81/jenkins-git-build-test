pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                echo 'Checking out code from Git...'
                // The Jenkins job will handle the checkout automatically if configured as a Pipeline script from SCM
                // But we can add explicit checkout if needed
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
                // For Python, build might just be setting up environment or checking syntax
                sh 'python -m py_compile app.py'
            }
        }
        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'python test_app.py'
            }
        }
    }
    
    post {
        success {
            echo 'Build and Test successful!'
        }
        failure {
            echo 'Build or Test failed!'
        }
    }
}
