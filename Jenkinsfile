pipeline {
    agent any

    stages {
        stage('Pre-build') {
            steps {
                echo 'Pre Building..'
                bash cf api $CF_API
                bash cf login -u $CF_USER -p $CF_PASS -o $CF_ORG -p $CF_SPACE
                bash cf apps
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
