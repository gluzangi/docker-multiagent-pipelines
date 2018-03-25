pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                    args  '-v /tmp:/tmp'
                    customWorkspace '/tmp/workx'
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
                    args  '-v /tmp:/tmp'
                    customWorkspace '/tmp/workx'
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
