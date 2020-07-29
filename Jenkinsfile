pipeline {

    agent any
      tools {
        maven 'apache-maven-3.6.3' 
    }
    
   
        stages{
         
            
        stage('Build') {
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
    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
        
        bat 'mvn sonar:sonar'
         }
       }
  }
    
            
            
            stage ('Artifactory') {
            steps {
                rtUpload (
                    serverId: 'art-1', // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
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
