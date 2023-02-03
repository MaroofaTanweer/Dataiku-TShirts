pipeline {
    agent {
        docker { image 'python:3.9.16-slim' }
    }
    stages {
        stage('PREPARE'){
			steps {
				script {
					sh "echo 'within branch: ${env.BRANCH_NAME}'"
					if(env.BRANCH_NAME.startsWith('feature_')) {
						echo 'within feature block'
						build job: 'Child-Job',
						parameters: [
							string(name: 'ENV_NAME', value: 'DEV')
						],
						wait: false
					} else if(env.BRANCH_NAME == 'release') {
						echo 'within release block'
						build job: 'Child-Job',
						parameters: [
							string(name: 'ENV_NAME', value: 'SIT')
						],
						wait: false
					} else if(env.BRANCH_NAME == 'master') {
						echo 'within master block'
						build job: 'Child-Job',parameters: [
							string(name: 'ENV_NAME', value: 'PROD')
						],
						wait: false
					} else {
						echo 'within else block'
					}
				}
            }
        }
    }
}
