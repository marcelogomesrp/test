pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    triggers {
        cron('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Realiza o checkout manualmente para permitir o uso do when
                    checkout scm
                }
            }
        }

        stage('Build') {
            when {
                expression {
                    // Verifica se a alteração foi uma tag
                    changeset ".*refs/tags/.*"
                }
            }

            steps {
                echo 'Build logic here'
            }
        }

	stage('prod') {
		steps {
			script {
				checkout scm
                    // Verifica se a alteração foi uma tag
                    if (env.CHANGE_ID.endsWith('tags')) {
                        echo 'Build logic here'
                    } else {
                        echo 'No build for non-tag changes'
                        currentBuild.result = 'ABORTED'
                    }

			}
		}
	}
    }
}

