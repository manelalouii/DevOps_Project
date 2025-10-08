pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Build') {
            steps {
                echo 'Pipeline lancé via webhook GitHub !'
            }
        }
    }
}
