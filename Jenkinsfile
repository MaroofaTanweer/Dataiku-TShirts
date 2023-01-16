pipeline {
    agent {
        docker { image 'python:3.9.16-slim' }
    }
    stages {
        stage('PREPARE'){
            steps {
                cleanWs()
                sh 'echo ${bundle_name}'
            }
        }
        stage('PACK_AND_PUB') {
            steps {
				sh 'echo PACK_AND_PUB'
            }
        }
        stage('DEV_TEST') {
            steps {
                sh 'echo DEV_TEST'
            }
        }
        stage('DEPLOY_TO_PROD') {
            steps {
                sh 'echo DEPLOY_TO_PROD'
            }
        }
    }
}
