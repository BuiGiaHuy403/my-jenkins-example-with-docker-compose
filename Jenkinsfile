pipeline {
    agent any 

    stages {
        stage("verify tooling"){
            steps{
                sh '''
                    docker version
                    docker info
                    docker compose version
                    curl --version 
                    sudo apt-get update && sudo apt-get install -y jq
                    jq --version
                '''
            }
        }
    }
}