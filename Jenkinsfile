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
                '''
            }
        }
        stage("Prune Docker Data"){
            steps {
                sh 'docker system prune -a --volumes -f'
            }
        }
        stage("Starting with Container"){
            steps{
                sh '''
                    docker compose up -d --no-color --wait
                    docker compose ps
                '''
            }
        }
        stage("Run tests against the container"){
            steps {
                sh 'curl https://localhost:3000/param?query=demo | jq'
            }
        }
    }
    post {
        always {
            sh 'docker compose down --remove-orphans -v'
            sh 'docker compose ps'
        }
    }
}