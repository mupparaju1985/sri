pipeline {
    agent any
        environment {
        	JOB_NAME = "${env.JOB_NAME}"    
		BRANCH_NAME = "${env.BRANCH_NAME}"    
		BUILD_NUMBER = "${env.BUILD_NUMBER}"   
            	COMMIT = "${env.GIT_COMMIT}"
		BUILD_URL ="${env.BUILD_URL}"
		JOB_NAME_FIRST = "${env.JOB_NAME}".split('/').first()
		JOB_NAME_LAST = "${env.JOB_NAME}".split('/').last()
	}
    stages {
    	stage('Deploy') {
	      input {
			message "Should we continue?"
	      }
	      steps {
			echo "Continuing with deployment"
	      }
        }
        stage('merge') {
            steps {
			echo " commit id $COMMIT"
		    	sh "git reset --hard HEAD~1"
		        sh "git push origin HEAD --force"
            }
        }
    }
}
