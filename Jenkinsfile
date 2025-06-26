pipeline{
    agent any

    stages{

        stage("Build and Test for Valid Branches"){

            when{
                anyOf {
                    branch  'main'
                    branch pattern: "feature/.*", comparator: "REGEXP"
                }
            }
            stages{

                stage("Checkout"){

                    steps{
                        checkout scm
                    }
                }
            
                stage("Restore Dependencies"){
                    steps{
                        sh 'dotnet restore'
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
                        sh 'dotnet build --no-restore'
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
                        sh 'dotnet test --no-build'
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