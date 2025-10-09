pipeline {
    agent any

    environment {
        IMAGE_NAME = "mon-app"
        IMAGE_TAG = "latest"
    }

    triggers {
        githubPush() // Déclenchement automatique quand un push est fait sur GitHub
    }

    stages {
        stage('Cloner le code depuis GitHub') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/manel']],
                    extensions: [],
                    gitTool: 'Default',
                    userRemoteConfigs: [[
                        credentialsId: 'githubtokenn',
                        url: 'https://github.com/manelalouii/DevOps_Project.git'
                    ]]
                )
            }
        }

        stage('Construire l\'image Docker') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Lister les images Docker') {
            steps {
                sh 'docker images'
            }
        }
    }

    post {
        success {
            echo 'Build terminé avec succès !'
        }
        failure {
            echo ' Le build a échoué.'
        }
    }
}
