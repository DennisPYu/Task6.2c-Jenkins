    pipeline{
        agent any
        environment{
            DIRECTORY_PATH = 'C:\\Users\\fudff\\Desktop\\BachelorL\\2023T1\\SIT223\\Task6.2c-Jenkins'
            TESTING_ENVIRONMENT = 'testing'
            PRODUCTION_ENVIRONMENT = 'DennisYu'
        }
        stages{
            stage('Build'){
                steps{
                    echo 'Fetch the source ode frome the $DIRECTORY_PATH'
                }
                post{
                    success{
                        echo 'Build Success'
                        mail to: "dennispfy@gmail.com",
                        subject: "Build Success",
                        body: "Build Success"
                    }
                    failure{
                        echo 'Build Failure'
                        mail to: "dennispfy@gmail.com",
                        subject: "Build Failure",
                        body: "Build Failure"
                    }
                }
            
            }
            
            stage('Test'){
                steps{
                    echo 'Unit Tests'
                    echo 'Integration Tests'
                }
            }

            stage('Code Quality Check'){
                steps{
                    echo 'Check th equalilty of the code'
                }
            }

            stage('Deploy'){
                steps{
                    echo "Deploy the application to a $TESTING_ENVIRONMENT environment"
                    }
            }
            
            stage('Approval'){
                steps{
                    echo 'Approval started and completed!'
                }
            }
            
            stage('Deploy to Production'){
                steps{
                    echo "Deploy the application to the $PRODUCTION_ENVIRONMENT environment"
                }
            }
            stage('Complete'){
                steps{
                    echo 'Deployment completed!'
                }
            }
        }
    }