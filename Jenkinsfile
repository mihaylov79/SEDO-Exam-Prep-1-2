pipeline{
    agent any

    stages{
        stage("Restore Dependencies"){
            steps{
                sh dotnet restore
            }
                 post{
                always{
                    echo "========Working========"
                }
                success{
                    echo "========Operation successfully finished========"
                }
                failure{
                    echo "========Operation failed========"
                }
            }
        }

        stage("Build Application"){
            steps{
                sh dotnet build --no restore
            }
            post{
                always{
                    echo "========Working========"
                }
                success{
                    echo "========Operation successfully finished========"
                }
                failure{
                    echo "========Operation failed========"
                }
            }
        }

        stage("Run Test"){
            steps{
                sh dotnet test --no build
            }
            post{
                always{
                    echo "========Working========"
                }
                success{
                    echo "========Operation successfully finished========"
                }
                failure{
                    echo "========Operation failed========"
                }
            }
        }


       
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}