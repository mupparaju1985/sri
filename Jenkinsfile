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
		         steps {
				script { 
					prevBuildLastCommitId()
				}
			}
        }
    }
}

def prevBuildLastCommitId() {
				def prev = currentBuild.previousBuild
				def items = null
				def result = null
				if (prev != null && prev.changeSets != null && prev.changeSets.size() && prev.changeSets[prev.changeSets.size() - 1].items.length) 	{
					items = prev.changeSets[prev.changeSets.size() - 1].items
					result = items[items.length - 1].commitId
					}
				println result
				return result
}
