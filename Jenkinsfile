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
    }
}
