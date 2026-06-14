pipeline {
    agent any

    environment {
        APP_SERVER = "172.31.23.96"
    }

    stage {

        stage('Checkout') {
    steps {
        git branch: 'main',
            url: 'https://github.com/msaditi19994/company-web-page-deployment.git'
    }

        stage('Deploy Website') {
            steps {
                sh """
                scp -o StrictHostKeyChecking=no index.html ec2-ubuntu@172.31.23.96:/tmp/
                ssh -o StrictHostKeyChecking=no ec2-ubuntu@172.31.25.146 'sudo cp /tmp/index.html /var/www/html/index.html'
                """
            }
        }
        }
    }
}
