pipeline {
    agent any
    tools {
        maven 'Maven_3.9'
        jdk 'JDK_17'
    }
    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Build') { steps { sh 'mvn clean package' } }
        stage('Test') { steps { sh 'mvn test' } }
        stage('Package') { steps { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true } }
        stage('Deploy') { steps { echo "Deploying application..." } }
    }
    post {
        success { echo "Pipeline completed successfully!" }
        failure { echo "Pipeline failed. Check logs." }
    }
}

