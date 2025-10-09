pipeline {
    agent any

    environment {
        IMAGE_NAME = 'mon-image'
        IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout Code') {
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

        stage('Build Java Project') {
            steps {
                dir('Order') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def image = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
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
