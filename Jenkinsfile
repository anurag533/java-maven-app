pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
    }
    environment {
  scannerHome  = "SonarQubeScanner"
}

    stages {
        stage('Compile stage') {
            steps {
                bat "mvn compile" 
        }
    }

         stage('testing stage') {
             steps {
                bat "mvn test"
        }
    }
        stage('SonarQube analysis') {

    withSonarQubeEnv('My SonarQube Server') { // If you have configured more than one global server connection, you can specify its name
      bat "${scannerHome}/bin/sonar-scanner"
    }
  }
   

     
    }
    }
