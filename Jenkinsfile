pipeline {
    agent any

    stages{
        stage('Remove existing containers'){
            steps{
                script{
                    echo "stopping existing container if any"
                    bat '''
                        docker compose down || echo "nothing to stop"
                    '''
                }
            }
        }

        stage('starting new container'){
            steps{
                script{
                    echo "starting container"
                    bat '''
                        docker compose up -d --build
                    '''
                }
            }
        }
    }

    post{
        success{
            echo "mission successful"
        }
        failure{
            echo "mission failed! retry"
        }
    }
}
