pipeline{
  agent any
  tools{
    maven 'Maven3'
  }
  stages{
    stage('CHECKOUT'){
      steps{
        git 'https://github.com/San05-git/newwslack.git'
      }
    }
    stage('Build'){
      steps{
        dir('newwslack'){
          bat 'mvn clean install'
        }
      }
    }
    stage('Test'){
      steps{
        dir('newwslack'){
          bat 'mvn test')
        }
      }
    }
  }
  
        
