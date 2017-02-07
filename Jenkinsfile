pipeline {
    agent any

    stages {
        withEnv(['ICD_WEBHOOK_URL=\'https://tc1:sc1@otcdm.mybluemix.net\'']) {
          stage('Build') {
            steps {
                echo 'Building dev..'
            }
          }
          stage('Test'){
            steps {
                echo 'Testing dev..'
            }
          }
          stage('Deploy') {
            steps {
                echo 'Deploying dev....'
            }
          }
          stage('IBM Continuous Delivery Connections') {
            steps {
                echo 'Creating connections...'
                sh 'curl -XPOST "$ICD_WEBHOOK_URL" -d \'{}\''
            }
          }
        }
    }
}
