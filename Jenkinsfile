pipeline {
    agent any
    stages {
        stage('Pull from GitHub') {
            steps {
                git credentialsId: 'your-credentials-id', url: 'https://github.com/Keerthana-Bindhurani/New-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-login-app .'
            }
        }
        stage('Push with Ansible') {
            steps {
                sh 'ansible-playbook -i hosts deploy.yml'
            }
        }
    }
}
