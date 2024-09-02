pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', changelog: false, credentialsId: 'gitHubToken', poll: false, url: 'https://github.com/DevOps24-Ashutosh/PythonToDoCICD.git'
            }
        }
    }
}