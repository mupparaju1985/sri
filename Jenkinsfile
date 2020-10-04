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
                sh "git checkout main"
                sh "git merge --ff-only -"
                sh "git push" 
                
            }
        }
    }
}
