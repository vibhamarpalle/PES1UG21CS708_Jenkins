pipeline {
    agent any
    
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/vibhamarpalle/PES1UG21CS708_Jenkins.git']]])
            }
        }
        
        stage('Build') {
            steps {
                sh 'g++ main.cpp -o output'
                build 'PES1UG21CS708-1'
            }
        }
        
        stage('Test') {
            steps {
                sh './output'
                sh 'test_error'
                 script {
                    def output = sh(script: './output', returnStdout: true).trim()
                    echo 'Output of main.cpp: ${output}'
                }
            }     
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
