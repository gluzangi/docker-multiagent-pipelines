pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -V'
            }
        }
        stage('Test') { 
            agent {
                docker {
                    image 'mariadb:latest' 
                }
            }
            steps {
                sh 'mysql --print-defaults' 
            }
            post {
                always {
                    echo 'Jenkins Says - I am done Yay!' 
                }
            }
        }
    }
}
