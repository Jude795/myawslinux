pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicdwebpage:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop webpage || true
                docker rm webpage || true
                docker run -d --name webpage -p 80:80 cicdwebpage:v1
                '''
            }
        }
    }
}
