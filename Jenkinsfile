pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Builld') {
            steps {
                echo 'Pipeline lancé via webhook GitHub !'
            }
        }
    }
}
