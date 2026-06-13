pipeline {
agent any
environment {
APP_SERVER = "172.31.23.66"
}
stages {
stage('checkout') {
steps {
git branch: 'main', url: 'https://github.com/msaditi19994/company-website.git'
}
stage('deploy website') {
steps {
sh """
scp -o StrictHostKeyChecking=no index.html ec2-user@${APP_SERVER}:/tmp/
ssh -o StrictHostKeyChecking=no ec2-user@${APP_SERVER} 'sudo cp /tmp/index.html /var/www/html/index.html'
"""
}
}
}
}