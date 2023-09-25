pipeline{
    agent any
    environment{
        DIRECTORY_PATH = '~./production/folder'
        TESTING_ENVIRONMENT = '~./testing/environment'
        PRODUCTION_ENVIRONMENT = '***Mitchell Bartolo***'
    }
    stages{
        stage('Build'){
            steps{
                echo "fetch the source code from the $DIRECTORY_PATH"
                echo "compile and package code using Maven"
            }
        }
        stage('Unit and Integration Tests'){
            
            steps{
                echo "initiating unit and integration tests using Selenium"
            }
            post{
                success{
                    emailext attachLog: true,
                        body: 'Unit and integration tests were successful',
                        subject: 'Unit and Integration Tests Notification - SUCCESS',
                        to: 'mitchell.bartolo@gmail.com'
                }
                failure{
                    emailext attachLog: true,
                        body: 'Unit and integration tests were not successful',
                        subject: 'Unit and Integration Tests Notification - FAILURE',
                        to: 'mitchell.bartolo@gmail.com'
                }
            }
        }
        stage('Code Analysis'){
            steps{
                echo "analysing code with CheckStyle"
            }
        }
        stage('Security Scan'){
            steps{
                echo "performing security scan with CodeQL"
            }
            post{
                success{
                    emailext attachLog: true,
                        body: 'Security scan was successful',
                        subject: 'Security Scan Notification - SUCCESS',
                        to: 'mitchell.bartolo@gmail.com'
                }
                failure{
                    emailext attachLog: true,
                        body: 'Security scan was not successful',
                        subject: 'Security Scan Notification - FAILURE',
                        to: 'mitchell.bartolo@gmail.com'
                }
            }
        }
        stage('Deploy to Staging'){
            steps{
                echo "deploying to AWS staging server"
            }
        }
        stage('Integration Tests on Staging'){
            steps{
                echo "performing integration tests on staging environment"
            }
            post{
                success{
                    emailext attachLog: true,
                        body: 'Integration tests on staging were successful',
                        subject: 'Integration Tests on Staging Notification - SUCCESS',
                        to: 'mitchell.bartolo@gmail.com'
                }
                failure{
                    emailext attachLog: true,
                        body: 'Integration tests on staging were not successful',
                        subject: 'Integration Tests on Staging Notification - FAILURE',
                        to: 'mitchell.bartolo@gmail.com'
                }
            }
        }
        stage('Deploy to Production'){
            steps{
                echo "Deploying to AWS production server"
            }
        }
    }
    post{
        success{
            emailext attachLog: true,
                body: 'Pipeline was successful',
                subject: 'Pipeline - SUCCESS',
                to: 'mitchell.bartolo@gmail.com'
        }
        failure{
            emailext attachLog: true,
                body: 'Pipeline was not successful',
                subject: 'Pipeline - FAILURE',
                to: 'mitchell.bartolo@gmail.com'
        } 
    }
}