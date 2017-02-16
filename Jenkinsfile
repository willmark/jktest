pipeline {
    agent any

    parameters {
       string(defaultValue: 'https://api.ng.bluemix.net', description: 'API endpoint', name: 'CF_API')
       string(defaultValue: 'Jenkins Broker Webhook', description: 'IBM Continuous Delivery Jenkins Broker webhook', name: 'ICD_WEBHOOK_URL')
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
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'set'
                sh 'git branch'
                sh 'git branch --contains 5cde6c5c9d04cddd25fbfc2c8fe2cca993eb1619'
                sh 'echo cf push jktest1 -m 64M -i 1'
                sh 'echo cf icd --create-connection $ICD_WEBHOOK_URL jktest1'
            }
        }
        stage('Delete') {
            steps {
                echo 'Deleting....'
                sh 'echo sleep 30'
                sh 'echo cf icd --delete-connection $ICD_WEBHOOK_URL jktest1'
                sh 'echo cf delete jktest1 -f'
            }
        }
    }
}
