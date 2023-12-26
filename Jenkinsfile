pipeline {
    
	agent any


	environment {
		def tag = sh(script: "git describe", returnStdout: true).trim()
		//def tagAnterior = sh(script: "git describe --tags \$(git rev-list --tags --max-count 1)", returnStdout: true).trim()
	}

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
				echo '-------> 9 master -'
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
	stage('eita tag') {
		when {
			buildingTag()
			beforeAgent true
		}
		steps {
			echo 'algo mudou a tag *****'
		}
	}

stage('tst 2') {
    steps {
        script {
            def tag = sh(script: "git describe", returnStdout: true).trim()
            echo env.tag
            if (env.TAG_NAME) {
                echo "trigged by th tag:"
                echo env.TAG_NAME
            } else {
                echo "trigger by branch, pr or ..."
            }
        }
    }
}





	}
}		
