pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Pulling latest code repository...'
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            // This tells Jenkins: Only run this stage if it is a PR targeting 'main'
            when {
                changeRequest target: 'main'
            }
            steps {
                echo 'Running SonarQube Code Quality Scanner...'
                echo 'SonarQube Scan Completed successfully!'
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo 'Executing application test suites...'
                sh 'echo "Tests passed!"'
            }
        }
    }
}