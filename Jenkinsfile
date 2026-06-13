pipeline {

agent any

environment {

APP_SERVER = "APP_SERVER_PRIVATE_IP"
}

stages {

stage('Checkout') {

steps {

git branch: 'main',
url: 'YOUR_GITHUB_REPO'
}
}

stage('Deploy Website') {

steps {

sshagent(['app-server-key']) {

sh """

scp \
index.html \
ubuntu@$APP_SERVER:/tmp/

ssh \
ubuntu@$APP_SERVER '

sudo cp /tmp/index.html \
/var/www/html/index.html

'

"""
}
}
}
}
}