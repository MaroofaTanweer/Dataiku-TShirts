pipeline {
    agent {
        docker { image 'python:3.9.16-slim' }
    }
    stages {
        stage('PREPARE'){
			steps {
                cleanWs()
				script {
					sh "echo 'within branch: ${env.BRANCH_NAME}'"
					if (env.BRANCH_NAME == 'master') {
						BRANCH_TO_TAG=env.BRANCH_NAME.replace('/','%2F')
						echo 'BRANCH_TO_TAG: ${BRANCH_TO_TAG}'
						build job: 'Child-Job', wait: false
					} else {
						echo 'within else block'
					}
				}
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
