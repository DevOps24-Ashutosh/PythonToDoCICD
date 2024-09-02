pipeline {
    agent any
    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        // stage('Checkout') {
        //     steps {
        //         git branch: 'main', changelog: false, credentialsId: 'gitHubToken', poll: false, url: 'https://github.com/DevOps24-Ashutosh/PythonToDoCICD.git'
        //     }
        // }
    }
}