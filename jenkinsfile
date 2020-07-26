pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
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
   

     
    }
    }
