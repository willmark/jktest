pipeline {
    agent any

    parameters {
       string(defaultValue: 'https://api.ng.bluemix.net', description: 'API endpoint', name: 'CF_API')
       string(defaultValue: 'DefaultBluemixOrganizationName', description: 'Bluemix organization name', name: 'CF_ORG')
       string(defaultValue: 'DefaultBluemixSpaceName', description: 'Bluemix space name', name: 'CF_SPACE')
    }

    environment {
        CF_CREDS = credentials("cf-user-creds")
    }

    stages {
        stage('Pre-build') {
            steps {
                echo 'Pre Building..'
                sh 'cf api $CF_API'
                sh 'cf login -u $CF_CREDS_USR -p $CF_CREDS_PSW -o $CF_ORG -s $CF_SPACE'
                sh 'cf icd -h'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test'){
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
