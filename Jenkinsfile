pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    stages {
        stage('CHECKOUT') {
            steps {
                git 'https://github.com/San05-git/newwslack.git'
            }
        }
        stage('Build') {
            steps {
                dir('newwslack') {
                    
                    bat 'mvn clean install'
                }
            }
        }
        stage('Test') {
            steps {
                dir('newwslack') {
                    bat 'mvn test'
                }
            }
        }
    }
    
    post {
        failure {
            slackSend(
                
                message: "FAILED: Job '${env.JOB_NAME}' [${env.BUILD_NUMBER}] (${env.BUILD_URL})"
            )
        }
        unstable {
            slackSend(
                
                message: "WARNING/UNSTABLE: Job '${env.JOB_NAME}' [${env.BUILD_NUMBER}] (${env.BUILD_URL})"
            )
        }
        success {
            slackSend(
               
                message: "SUCCESS: Job '${env.JOB_NAME}' [${env.BUILD_NUMBER}] (${env.BUILD_URL})"
            )
        }
    }
}
