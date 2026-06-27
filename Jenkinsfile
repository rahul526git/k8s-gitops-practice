pipeline {
    agent any

    tools {
        jdk 'Java 17' // UPDATED: Compiles the incoming feature branch using JDK 17
        maven 'Maven 3'
    }

    stages {
        stage('Git Checkout') {
            steps {
                echo 'Checking out official production code from main branch...'
                git branch: 'citesting', credentialsId: 'jenkins-user', url: 'https://github.com/rahul526git/k8s-gitops-practice'
            }
        }


        stage('Maven Build & Test') {
            steps {
                echo 'Compiling Java code and packaging the JAR file...'
                dir('java-app') {
                    sh 'mvn clean package'
                }
            }
        }

        
        stage('Simulated Delay') {
            steps {
                echo 'Simulating a long-running build step...'
                // Sleep for 300 seconds (5 minutes)
                sh 'sleep 600'
            }
        }


        stage('3. Verify Dockerfile Compilation') {
            steps {
                echo 'Testing multi-stage Docker build integrity (No Push)...'
                dir('java-app') {
                    sh "docker build -t pr-citesting-build:${env.BUILD_NUMBER} ."
                }
            }
        }
    }

    post {
        always {
            echo 'Clearing PR build workspace footprint...'
            cleanWs()
        }
    }
}
