pipeline {
    agent any

    tools {
        jdk 'Java 17' // UPDATED: Compiles the incoming feature branch using JDK 17
        maven 'Maven 3'
    }

    stages {
        stage('1. Checkout Feature Branch') {
            steps {
                echo 'Dynamically checking out the incoming PR/feature branch...'
                checkout scm
            }
        }

        stage('2. Run Target Unit Tests') {
            steps {
                echo 'Executing unit tests using Java 17 runtime environment...'
                dir('java-app') {
                    sh 'mvn clean test'
                }
            }
        }

        stage('3. Verify Dockerfile Compilation') {
            steps {
                echo 'Testing multi-stage Docker build integrity (No Push)...'
                dir('java-app') {
                    sh "docker build -t pr-test-build:${env.BUILD_NUMBER} ."
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
