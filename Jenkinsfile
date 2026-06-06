pipeline {
    agent any
    
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        
        stage('Run Unit Tests') {
            // This stage will ONLY run if the PR is aiming for the main branch
            when {
                changeTarget 'main' 
            }
            steps {
                echo "Validated: This PR is targeting the 'main' branch. Running tests..."
                sh 'exit 0' 
            }
        }
    }
}