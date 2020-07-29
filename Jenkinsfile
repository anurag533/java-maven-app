pipeline {

    agent any
    
   
        stages{
            stage("Code Checkout") {
                	steps {
                		git branch: 'master',
                		url: 'https://github.com/kapilnegi98/java-maven-app.git'
                  	}
              }
            
        stage('Build') {
            steps{
   
       bat 'mvn package'
 
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
                                        "pattern": "target/*.war",
                                        "target": "kapil/"
                                    }
                                ]
                            }"""
                )
            }
        }
        }
    
    }
