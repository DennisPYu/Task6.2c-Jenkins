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
                    echo 'Compile and package files from the $DIRECTORY_PATH using Maven'
                }
            
            }
            
            stage('Unit and Integration Tests'){
                steps{
                    echo 'Unit Tests by Citrus'
                    echo 'Integration Tests by Citrus '
                }
                post{
                    success{
                            echo 'Unit and Integration Tests Success'
                            emailext to: 'dennispfy@gmail.com',
                            subject: 'Unit and Integration Tests',
                            body: 'Unit and Integration Tests successfully passed, logs attached',
                            attachLog: true
                            }
                    failure{
                                echo 'Unit and Integration Tests Failed'
                                emailext to: 'dennispfy@gmail.com',
                                subject: 'Unit and Integration Tests',
                                body: 'Unit and Integration Tests failed, logs attached',
                                attachLog: true
                    
                            }
                    }
            }

            stage('Code Analysis'){
                steps{
                    echo 'Check th equalilty of the code by SonarQube'
                }
            }

            stage('Security Scan'){
                steps{
                    echo "Check the security of the code by Checkmarx"
                    }

                post{

                    success{
                        echo 'Security Scan Success'
                        emailext to: 'dennispfy@gmail.com',
                        subject: 'Security Scan',
                        body: 'Security Scan successfully passed, logs attached',
                        attachLog: true
                        }

                    failure{
                        echo 'Security Scan Failed'
                        emailext to: 'dennispfy@gmail.com',
                        subject: 'Security Scan',
                        body: 'Security Scan failed, logs attached',
                        attachLog: true
                        }
                }
            }   
            
            stage('Deploy to staging'){
                steps{
                    echo 'Deploy the application to the AWS $TESTING_ENVIRONMENT environment'
                }
            }
            
            stage('Integration Tests on Staging'){
                steps{
                    echo "Run integration tests on the TESTING_ENVIRONMENT environment"
                }
            }
            stage('Deploy to production'){
                steps{
                    echo 'Deploy the application to the AWS $PRODUCTION_ENVIRONMENT environment'
                }
            }
        }
    }