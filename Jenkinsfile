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
				echo '-------> 2'
			}
		}
		stage('Step2 master only') {
			when {
               expression { env.BRANCH_NAME == "master"}
			}
			steps {
			    echo 'step 2 B'                
			}
		}
		stage('Step3') {
			steps {
				echo 'step 3'
				sh 'printenv'
			}
		}
	}
}		
