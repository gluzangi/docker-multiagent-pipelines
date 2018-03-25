pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'php:cli'
                    args  '-v /tmp:/tmp'
                    /* customWorkspace '/tmp/workx' */
                }
            }
            steps {
                sh 'ls -al ./'
                sh 'php -m | tee -a /tmp/php-modules.out'
                sh 'ls -al /tmp/'
            }
        }
        stage('Test') { 
            agent {
                docker {
                    image 'mariadb:latest' 
                    args  '-v /tmp:/tmp'
                    /* customWorkspace '/tmp/workx' */
                }
            }
            steps {
                sh 'ls -al ./'
                sh 'mysql --print-defaults | tee -a /tmp/mysql-defaults.out'
                sh 'ls -al /tmp/'
            }
            post {
                always {
                    echo 'Jenkins Says - I am done Yay!' 
                }
            }
        }
    }
}
