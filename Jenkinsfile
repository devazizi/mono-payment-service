pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh docker build -t paymentCoreService:latest .
                sh docker image push registery.monopayment.local:5000/myadmin/paymentCoreService:latest
            }
        }
        stage('Test') {
            steps {
                sh docker run --rm php paymentCoreService:latest bash -c "php artisan test"
            }
        }
        stage('Deploy') {
            steps {
                sh cd var/www/html; docker-compose up -d
            }
        }
    }
}
