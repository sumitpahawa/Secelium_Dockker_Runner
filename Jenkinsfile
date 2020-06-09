pipeline{
    agent any
    stages{
        stage("Pull latest images"){
            steps{
                sh "docker pull sumit2506/selenium-docker"

            }
        }
        stage("Start Grid"){
            steps{
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("RUN TEST"){
            steps{
            sh "docker-compose up book-module search-module"
            }
        }

    }
    post{
        always {
            archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
        }
    }
}