pipeline {
    agent any 
    stages {
        stage('removing old files') { 
            steps {

                sh "sudo rm -rvf /var/www/html/*"
                sh "sudo rm -rvf /var/www/html/.git*"
                sh "sudo rm -rvf /var/www/html/.e*"
                sh "sudo rm -rvf /var/www/html/.s*"
                
            }
        }
        stage('Cloning repo') { 
            steps {
              
                sh "sudo git clone https://github.com/pemba3690/php.git /var/www/html/"
                sh " sudo php artisan migrate "
                sh " sudo php artisan db:seed "
                sh " sudo php artisan storage:link "
                //
            }
        }
        stage('Reloading code') { 
            steps {
                sh "sudo systemctl reload httpd"
                sh " sudo php artisan serve "
            }
        }
    }
}

