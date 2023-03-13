pipeline{

    agent any

    tools {
        maven 'maven'
    }

    stages{
        stage("test on local machine"){
            steps{
               bat 'mvn test'
                }
            }
            stage("BUILD .WAR FILE"){
            steps{
               bat 'mvn package'
                 }
             }
        }
        
   
}
