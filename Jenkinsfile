pipeline {
    agent any
    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout') {
            steps {
                git branch: 'main', changelog: false, credentialsId: 'gitHubToken', poll: false, url: 'https://github.com/DevOps24-Ashutosh/PythonToDoCICD.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '''
                echo "Building Docker Image from the Repos Dockerfile"
                docker build -t ashuto91/pytodo:${BUILD_NUMBER} .
                '''
            }
        }
    }
}