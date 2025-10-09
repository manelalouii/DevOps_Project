pipeline {
    agent any

    environment {
        IMAGE_NAME = "mon-app"
        IMAGE_TAG = "latest"
    }

    stages {
        stage('git') {
            steps {
               checkout scmGit(branches: [[name: '*/manel']], 
               extensions: [], gitTool: 'Default', 
               userRemoteConfigs: [[credentialsId: 'githubtokenn', 
               url: 'https://github.com/manelalouii/DevOps_Project.git']])
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
