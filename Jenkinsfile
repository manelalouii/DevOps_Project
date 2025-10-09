pipeline {
    agent any

    stages {
        stage('Checkout Codeee') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/manel']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    gitTool: 'Default',
                    userRemoteConfigs: [[
                        credentialsId: 'githubtokenn',
                        url: 'https://github.com/manelalouii/DevOps_Project.git'
                    ]]
                ])
            }
        }
        stage('Build Docker Image') {
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
}
