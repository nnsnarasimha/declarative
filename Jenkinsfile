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
                sh 'rm -rf /var/www/html/*'
                sh 'git clone https://github.com/nnsnarasimha/websites.git /var/www/html'
            }
        }
    }
}
