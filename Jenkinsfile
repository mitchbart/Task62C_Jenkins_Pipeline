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
                // always{
                //     mail to: "mitchell.bartolo@gmail.com",
                //     subject: "Unit and Integration Tests Notification - SUCCESS",
                //     body: "Unit and integration tests were successful"
                //     //body:'''Hi, Please find below. ${BUILD_LOG_REGEX, regex="Project name:", linesBefore=0, linesAfter=10, maxMatches=5, showTruncatedLines=false, escapeHtml=true} Regards, DT ''',
                // }
                always{
                    emailext body: 'Test Message',
                        subject: 'Test Subject',
                        to: 'mitchell.bartolo@gmail.com'
                    //body:'''Hi, Please find below. ${BUILD_LOG_REGEX, regex="Project name:", linesBefore=0, linesAfter=10, maxMatches=5, showTruncatedLines=false, escapeHtml=true} Regards, DT ''',
                }
                failure{
                    mail to: "mitchell.bartolo@gmail.com",
                    subject: "Unit and Integration Tests Notification - FAILURE",
                    body: "Unit and integration tests failed"
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
                always{
                    mail to: "mitchell.bartolo@gmail.com",
                    subject: "Security Scan Notification - SUCCESS",
                    body: "Security scan was successful"
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
                always{
                    mail to: "mitchell.bartolo@gmail.com",
                    subject: "Integration Tests on Staging Notification - SUCCESS",
                    body: "Integration tests on staging were successful"
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
            mail to: "mitchell.bartolo@gmail.com",
            subject: "Pipeline was successful",
            body: "Unit and integration tests were successful"
        }
    }
}