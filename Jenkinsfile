pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
    }
        stages{
        stage('build') {
            steps{
   
       bat 'mvn clean install'
 
            }
  }


        stage('SonarQube analysis') {
            steps{
    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
        
        bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
         }
        }
  }
    }
   

     
    
    }
