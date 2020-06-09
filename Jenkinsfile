pipeline{
    agent any
    stages{
        stage("Pull latest images"){
            steps{
                sh "docker pull sumit2506/selemiun-docker"

            }
        }
        stage("Start Grid"){
            steps{
                sh "docker-compose up -d hun chrome firefox"
            }
        }
        stage("RUN TEST"){
            steps{
            sh "docker-compose up search-module book-flight-module"
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