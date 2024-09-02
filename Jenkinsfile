pipeline {
    agent any
    environment {
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
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
        stage("Push docker Image to DockerHub") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerHubCred', passwordVariable: 'DockerHub-Password', usernameVariable: 'DockerHub-Username')]) {
                    sh 'docker login -u $DockerHub-Username -p $DockerHub-Password'   
                }
                sh '''
                echo "Pushing the docker Image built in previous Images is being push to docker hub"
                docker push ashuto91/pytodo:${BUILD_NUMBER}
                '''
            }
        }
        stage("Removing the previous Build Image") {
            steps {
                sh '''
                echo "Removing the previous built image"
                docker rmi ashuto91/pytodo:${BUILD_NUMBER}
                '''
            }
        }
    }
}