pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World1'
                echo 'Hello World2'
                echo 'Hello World3'
            }
        }

        stage('checkout'){
            steps {
                //    checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/priyabuss2004/java-project.git']])  
                echo "checkout completed"    
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


        stage('Executing Tests'){
            steps {
                sh """
                       echo "-------------Executing Testcases------------------"
                       mvn test
                       echo "-------------Testccases Execution Completed---------"
                """
              
           }  
      }
    
    }
}   
