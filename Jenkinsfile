pipeline {
    agent any
    stages {

        stage('Check Docker') {
            steps {
                sh 'which docker && docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('java-login-app') { // adjust path if your Dockerfile is deeper
                    sh 'docker build -t java-login-app .'
                }
            }
        }

        stage('Push with Ansible') {
            steps {
                sh 'ansible-playbook -i hosts deploy.yml'
            }
        }
    }
}
