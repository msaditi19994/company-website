pipeline {
    agent any
    
    environment {
        APP_SERVER = "100.53.179.5"
        
        APP_USER = "ec2-user"
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/msaditi1994/company-website.git',
                    credentialsId: 'app-server-key'  
            }
        }
        
        stage('Deploy to EC2') {
            steps {
                sshagent(credentials: ['app-server-key']) {  // 3. Must match Jenkins Credentials ID exactly
                    sh """
                        echo "Deploying index.html to ${APP_SERVER}"
                        scp -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null index.html ${APP_USER}@${APP_SERVER}:/tmp/
                        ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ${APP_USER}@${APP_SERVER} 'sudo cp /tmp/index.html /var/www/html/index.html && sudo systemctl restart httpd'
                    """
                }
            }
        }
    }
}
