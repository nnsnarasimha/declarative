pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
              checkout([$class: 'GitSCM', 
                branches: [[name: '*/main']],
                doGenerateSubmoduleConfigurations: false,
                extensions: [[$class: 'CleanCheckout']],
                submoduleCfg: [], 
                userRemoteConfigs: [[url: 'https://github.com/nnsnarasimha/websitedeployment.git']]])
              sh "ls -ltr"
          }
        }
        stage('Dev'){
            steps {
                sh 'sudo rm -rf /var/www/html/*'
                sh 'sudo rm -rf /var/www/html/.git'
                sh 'sudo systemctl start httpd'
                sh 'sudo git clone https://github.com/nnsnarasimha/websites.git /var/www/html'
            }
        }
    }
}
