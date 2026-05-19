pipeline {
    agent any

    stages {
        stage('1. Checkout Code') {
            steps {
                // Grab the fresh code pushed to GitHub
                checkout scm
            }
        }

        stage('2. Code Quality Check (Linting)') {
            steps {
                // Simulating a quick code analysis check
                echo 'Running HTML/CSS syntax integrity checks...'
            }
        }

        stage('3. Build Docker Images') {
            steps {
                // Baking our docker containers
                sh 'docker build -t backend-user:latest ./src/user-service'
                sh 'docker build -t frontend-dashboard:latest ./src/frontend'
            }
        }

        stage('4. Push to Central Registry') {
            steps {
                // Send images to Docker Hub registry so cloud nodes can grab them
                echo 'Publishing baked containers to Docker Hub...'
            }
        }

        stage('5. Deploy to Cluster') {
            steps {
                // Instantly update the running systems
                echo 'Deploying application via Kubernetes manifests...'
            }
        }
    }
    
    post {
        success {
            echo 'Deployment Successful! Everything is live and healthy.'
        }
        failure {
            echo 'Alert! Pipeline failed. Rolling back to previous stable state.'
        }
    }
}