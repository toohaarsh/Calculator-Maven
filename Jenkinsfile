pipeline {
    agent any

    tools {
        maven 'Maven-3.9.9'  // Make sure this matches your Jenkins Maven installation name
    }

    environment {
        GIT_URL = 'https://github.com/YOUR_USERNAME/Calculator-Maven.git'
        BRANCH_NAME = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code...'
                git branch: "${BRANCH_NAME}", url: "${GIT_URL}"
            }
        }

        stage('Clean') {
            steps {
                echo 'Cleaning the project...'
                sh 'mvn clean'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling the project...'
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build and tests were successful!'
        }
        failure {
            echo 'Build or tests failed. Check console output for details.'
        }
    }
}
