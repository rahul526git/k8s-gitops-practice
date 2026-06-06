pipeline {
    agent any
    
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                echo 'Running Application Unit Tests...'
                // Simulate running tests. Change to 'exit 1' to practice a failure!
                sh 'exit 0' 
            }
        }
    }
    
    post {
        success {
            echo 'Tests passed! Notifying GitHub...'
            // This tells GitHub the PR is safe to merge
        }
        failure {
            echo 'Tests failed! Locking GitHub PR...'
            // This keeps the GitHub PR locked
        }
    }
}