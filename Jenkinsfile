pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the Docker image...'
                    sh 'docker build -t simple-flask-app .'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    echo 'Running simple tests...'
                    sh 'docker run --rm simple-flask-app curl -f http://localhost:5000 || exit 1'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying the application...'
                    // Add deployment steps here (e.g., push to a registry)
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh 'docker system prune -f'
        }
    }
}
