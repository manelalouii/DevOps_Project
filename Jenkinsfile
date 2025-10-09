pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Build') {
            steps {
                echo 'Pipeline lancé via webhook GitHub !'
                // ajoute ici tes étapes réelles, par exemple :
                // sh 'make build'
                // sh 'npm install && npm test'
            }
        }
    }

    post {
        success {
            echo 'Build réussi'
        }
        failure {
            echo 'Build échouéeeeeee'
        }
    }
}
