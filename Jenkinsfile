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
		    sh 'ls -la'
   		    sh 'git log -n 1 --pretty=format:"%H %an %ae %s"'
                }
            }
        }

	stage('ah'){
		steps {
			sh 'printenv'
		}
	}

        stage('Print Environment Variables') {
            steps {
                script {
                    env.each { key, value ->
                        echo "Variable: ${key}, Value: ${value}"
                    }
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
		    echo env.CHANGE_ID
		    echo env.BRANCH_NAME
		    echo env.GIT_COMMIT
		    echo  "${env.GIT_BRANCH}-${BUILD_ID}"


			}
		}
	}
    }
}

