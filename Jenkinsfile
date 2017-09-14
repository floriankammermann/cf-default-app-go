pipeline {
    agent {label 'master'}

    stages {
        stage('Deploy') {
            steps {

            withCredentials([usernamePassword(credentialsId: 'cf-tech-user', passwordVariable: 'CF_PASSWORD', usernameVariable: 'CF_USER')]) {
                   sh 'cf api https://api.scapp-console.swisscom.com --skip-ssl-validation'
                   sh 'cf auth $CF_USER  $CF_PASSWORD'
                   sh 'cf target -o INI-DEV-FDN_Jarvis -s Test'
                   sh 'cf push unicorns-go-app'
               }
            }
        }
    }
}
