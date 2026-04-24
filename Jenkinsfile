pipeline {
    agent any
    
    parameters {
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run the test stage?')
        stringParam(name: 'VERSION', defaultValue: '1.0.0', description: 'Application version to deploy')
        choiceParam(name: 'ENVIRONMENT', choices: ['development', 'staging', 'production'], description: 'Deployment environment')
    }
    
    environment {
        APP_NAME = 'MySecureApp'
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Building ${APP_NAME} version ${params.VERSION}"
                echo "Environment: ${params.ENVIRONMENT}"
            }
        }
        
        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo "Testing ${APP_NAME} version ${params.VERSION}"
                echo "Running all test suites..."
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying ${APP_NAME} version ${params.VERSION} to ${params.ENVIRONMENT}"
            }
        }
        
        stage('Info') {
            steps {
                echo "Build number: ${env.BUILD_NUMBER}"
                echo "Job name: ${env.JOB_NAME}"
                echo "Branch: ${env.BRANCH_NAME}"
                echo "Execute Tests: ${params.executeTests}"
                echo "Version: ${params.VERSION}"
                echo "Environment: ${params.ENVIRONMENT}"
            }
        }
    }
    
    post {
        always {
            echo "Pipeline execution finished for ${APP_NAME}"
        }
        success {
            echo '✅ Pipeline succeeded!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
