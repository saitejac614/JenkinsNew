pipeline {
    agent any 
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/saitejac614/JenkinsNew.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                script {
                    echo 'Building the Docker image...'
                    sh 'docker build -t saitejac614/jenkins-app:latest .'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    echo 'Pushing the Docker image to Docker Hub...'
                    sh 'docker push saitejac614/jenkins-app:latest'
                }
            }
        }
        stage('Cleanup') {
            steps {
                echo 'Cleaning up...'
                sh 'docker system prune -f'
            }
        }
    }
}
