pipeline {
    agent any


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
