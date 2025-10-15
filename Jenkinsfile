pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'  // Ensure this matches the name in Jenkins
    }

    environment {
        IMAGE_NAME = 'mon-image'
        IMAGE_TAG = 'latest'
        JAVA_HOME = "${tool 'JAVA_HOME'}"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Codeeee') {
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
       
     stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') { 
                    dir('Order') {
                        sh 'mvn sonar:sonar -Dsonar.projectKey=devops_project -Dsonar.projectName=devops_project'
                    }
                }
            }
        }


        stage('Build Docker Image') {
            steps {
                dir('Order') {
                    script {
                        def image = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                    }
                }
            }
        }

        stage('List Docker Images') {
            steps {
                sh 'docker images'
            }
        }
    }
}
