pipeline {

	agent any
	stages {
        
        stage('init') {
            steps{
                script{
                    if (env.GIT_BRANCH ==~ /.*stage/) {
                        env.ENVIRONMENT = "hml"
                        env.TESTE =  "UM_STAGE"
                    } else if (env.GIT_BRANCH ==~ /.*master/) {
                        env.ENVIRONMENT = "prd"
                        env.TESTE =  "PRODUCAO"
                    } else {
                        env.ENVIRONMENT = "test"
                        env.TESTE =  "QUALQUER OUTRA COISA"
                    }
                }

            }
        }

		stage('Step1') {
			steps {
				echo 'step 1'
			}
		}
		stage('Step2 - Parallel In Sequential') {		    
			steps {
			    echo 'step 2 B'
                sh 'printenv'                    
			}
		}
		stage('master') {
            when { expression { env.BRANCH_NAME == "master" } }
			steps {
				echo 'aqui so master'
			}
		}
	}
}		