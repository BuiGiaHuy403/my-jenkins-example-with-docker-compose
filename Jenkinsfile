pipeline {
    agent any 

        
    stages {
         stage('Install jq') {
            steps {
                sh '''
                    sudo apt-get update && sudo apt-get install -y jq
                '''
            }
        }
        stage("verify tooling"){
            steps{
                sh '''
                    docker version
                    docker info
                    docker compose version
                    curl --version 
                    jq --version
                '''
            }
        }
       
    }
}