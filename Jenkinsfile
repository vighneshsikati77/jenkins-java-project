pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('checkout'){
            steps {
                    checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/priyabuss2004/java-project.git']])  
                 }  
      }

     stage('Building Application'){
            steps {
                sh """
                       echo "-------------Building Application------------------"
                       mvn clean package
                       echo "-------------Application Built Successfully---------"
                """
              
           }  
      }
    
    }
}   
