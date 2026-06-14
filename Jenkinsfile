pipeline {

agent any

environment {

APP_SERVER = "172.31.23.96"
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
ubuntu@$172.31.23.96:/tmp/

ssh \
ubuntu@$172.31.23.96'

sudo cp /tmp/index.html \
/var/www/html/index.html

'

"""
}
}
}
}
}
