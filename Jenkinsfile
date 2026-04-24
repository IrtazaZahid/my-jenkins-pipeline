pipeline {
    agent any
    
    environment {
        APP_NAME = 'MySecureApp'
        APP_VERSION = '1.0.0'
        BUILD_ENV = 'development'
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Building ${APP_NAME} version ${APP_VERSION}"
                echo "Environment: ${BUILD_ENV}"
            }
        }
        
        stage('Test') {
            when {
                branch 'main'
            }
            steps {
                echo "Testing ${APP_NAME} version ${APP_VERSION}"
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying ${APP_NAME} version ${APP_VERSION} to ${BUILD_ENV}"
            }
        }
        
        stage('Info') {
            steps {
                echo "Build number: ${env.BUILD_NUMBER}"
                echo "Job name: ${env.JOB_NAME}"
                echo "Branch: ${env.BRANCH_NAME}"
                echo "Workspace: ${env.WORKSPACE}"
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
