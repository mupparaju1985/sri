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
                sh 'git tag -a tagName -m "Your tag comment"
                sh 'git merge dev'
                sh 'git commit -am "Merged develop branch to master'
                sh "git push origin main"
                
            }
        }
    }
}
