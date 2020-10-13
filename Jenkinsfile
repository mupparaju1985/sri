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
	TEMP_DIR = ''
	}
    stages {
    	stage('Deploy') {
		         steps {
				script { 
					sh "mkdir -p $BUILD_NUMBER"
					def workspace = WORKSPACE
					workspace = env.WORKSPACE
					echo "Current workspace is ${env.WORKSPACE}"
					def changeLogSets = currentBuild.changeSets
					for (int i = 0; i < changeLogSets.size(); i++) {
    						def entries = changeLogSets[i].items
    						for (int j = 0; j < entries.length; j++) {
        						def entry = entries[j]
        						echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
        						def files = new ArrayList(entry.affectedFiles)
        						for (int k = 0; k < files.size(); k++) {
            							def file = files[k]
            							echo "  ${file.editType.name} ${file.path}" 
								sh "echo ${file.path} >>${env.WORKSPACE}/$BUILD_NUMBER/te.txt "
								echo "${env.WORKSPACE}/${file.path}"
								echo "${env.WORKSPACE}/$BUILD_NUMBER"
							}
						}
					}
				}
			}
		}
	}
}
