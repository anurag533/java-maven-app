pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
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
