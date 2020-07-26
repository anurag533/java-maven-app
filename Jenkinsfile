pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
    }
        stage('build') {
            steps{
    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
         withMaven(maven:'apache-maven-3.6.3') {
       bat 'mvn clean install'
         }
    }
            }
  }

    stages{
        stage('SonarQube analysis') {
            steps{
    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
         withMaven(maven:'apache-maven-3.6.3') {
       bat 'sonar:sonar'
         }
    }
            }
  }
    }
   

     
    
    }
