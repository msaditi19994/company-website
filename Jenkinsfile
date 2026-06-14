pipeline {
agent any
environment {
   APP_SERVER = "172.31.25.146"
}
stages {
stage('checkout') {
steps {
git branch: 'main', url: 'https://github.com/msaditi19994/company-website.git'
}
}
stage('deploy website') {
steps {
sshagent(credentials: ['app-server-key']) {
sh """
scp -o StrictHostKeyChecking=no index.html ubuntu@${APP_SERVER}:/tmp/
ssh -o StrictHostKeyChecking=no ubuntu@${APP_SERVER} 'sudo cp /tmp/index.html /var/www/html/index.html'
"""
}
}
}
}
}
