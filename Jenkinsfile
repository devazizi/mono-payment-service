pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                docker build -t paymentCoreService:latest .
                docker image push registery.monopayment.local:5000/myadmin/paymentCoreService:latest
            }
        }
        stage('Test') {
            steps {
                docker run --rm php paymentCoreService:latest bash -c "php artisan test"
            }
        }
        stage('Deploy') {
            steps {
                cd var/www/html; docker-compose up -d
            }
        }
    }
}
