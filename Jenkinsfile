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
                sh "git checkout dev"
                sh "git merge --ff-only origin main"
                sh "git push" 
                
            }
        }
    }
}
