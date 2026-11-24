pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Server') {
            steps {
                sh 'docker build -t mern-server ./Server'
            }
        }
        stage('Build Client') {
            steps {
                sh 'docker build -t mern-client ./Client'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker compose -p myappreact down || true'
                sh 'docker compose -p myappreact up -d'
            }
        }
        stage('Test') {
            steps {
                sh 'sleep 5'
                sh 'docker exec mern-server wget -qO- http://localhost:9000/api/health'
            }
        }
    }

    post {
        success { echo 'Application deployee avec succes !' }
        failure { echo 'Echec du pipeline' }
    }
}
