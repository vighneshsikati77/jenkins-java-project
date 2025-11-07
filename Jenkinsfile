pipeline {
    agent any
    parameters {
      string(name: "App_Version", description: "provide application version")
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World1'
                echo 'Hello World2'
                echo 'Hello World3'
                 echo 'Hello World4'
                 echo 'Hello World5'
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


      stage('Acceptance'){
            steps {
            //  input 'Proceed'
                echo "Proceed"
           }  
      }


       stage('Building the Image'){
            steps {
              sh """
                 echo "---------------Building Docker Image-----------"
                 docker build -t priya123456/myjavaapp:"${App_Version}" .
                 echo "---------------Completed Pusing Docker Image-----------"
                 """
           }  
      }  

        stage('Scanning the Image'){
            steps {
              sh """
                 echo "---------------Scanning Docker Image-----------"
                 trivy image priya123456/myjavaapp:"${App_Version}" > scan.txt
                 cat scan.txt
                 echo "---------------Completed Scanning Docker Image-----------"
                 """
           }  
      }  
    
    }
}   
