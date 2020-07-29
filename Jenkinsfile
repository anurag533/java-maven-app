pipeline {

    agent any
      tools {
        maven 'apache-maven-3.6.3' 
    }
    
   
        stages{
         
            
        stage('Build stage') {
            steps{
   
       bat 'mvn package'
 
            }
  }
            
            
         stage('testing stage') {
             steps {
                bat "mvn test"
        }
    }
               
            
                   stage('SonarQube analysis') {
           steps{
    withSonarQubeEnv('sonarqube') { 
        
        bat 'mvn sonar:sonar'
         }
       }
  }
    
            
            
            stage ('Artifactory') {
            steps {
                rtUpload (
                    serverId: 'art-1', 
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "*/*.war",
                                        "target": "kapil/"
                                    }
                                ]
                            }"""
                )
            }
        }
        }
    
    }
