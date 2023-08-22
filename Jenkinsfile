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
                echo "compile the code and generate any necessary artifacts"
            }
            post{
                success{
                    mail to: "mitchell.bartolo@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was successful"
                }
            }
        }
        stage('Test'){
            steps{
                echo "unit tests"
                echo "integration tests"
            }
        }
        stage('Code Quality Check'){
            steps{
                echo "check the quality of the code"
            }
        }
        stage('Deploy'){
            steps{
                echo "deploy the application to $TESTING_ENVIRONMENT"
            }
        }
        stage('Approval'){
            steps{
                sleep(time: 10)
            }
        }
        stage('Deploy to Production'){
            steps{
                echo "Deploying to production environment $PRODUCTION_ENVIRONMENT"
            }
        }
        stage('Complete'){
            steps{
                echo "Deploying to production environment $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}