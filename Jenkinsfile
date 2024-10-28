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
            withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]) {
                sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                sh 'docker push saitejac614/jenkins-app:latest'
            }
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
