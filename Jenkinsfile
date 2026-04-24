pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        
        stage('Test') {
            when {
                branch 'main'
            }
            steps {
                echo 'Testing.. (only on main branch)'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline execution finished'
        }
        success {
            echo '✅ Pipeline succeeded!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
