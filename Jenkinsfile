pipeline {
	agent any
	stages {
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
		stage('Step3') {
			steps {
				echo 'step 3'
			}
		}
	}
}		