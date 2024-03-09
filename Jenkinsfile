pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/shaugrin/PES1UG21CS181_Jenkins.git']]])
            }
        }

        stage('Build') {
            steps {
                build 'PES1UG21CS181-1'
                sh 'g++ main.cpp -o output'
            }
        }

        stage('Test') {
            steps {
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying...'
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed.'
        }
    }
}
