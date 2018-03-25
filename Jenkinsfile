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
                sh 'php -m | tee -a /tmp/php-modules.out'
                sh 'ls -al ./'
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
                sh 'mysql --print-defaults | tee -a /tmp/mysql-defaults.out'
                sh 'ls -al ./'
            }
            post {
                always {
                    echo 'Jenkins Says - I am done Yay!' 
                }
            }
        }
    }
}
