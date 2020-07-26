pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
    }
    environment {
  scannerHome  = "SonarQubeScanner"
}

    stages{
        stage('SonarQube analysis') {
            steps{
    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
      bat "${scannerHome}/bin/sonar-scanner"
    }
            }
  }
    }
   

     
    
    }
