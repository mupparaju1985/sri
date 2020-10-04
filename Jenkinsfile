pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('merge') {
            steps {
                bat "git checkout dev"
                bat "git merge --ff-only -"
                bat "git push" 
                
            }
        }
    }
}
