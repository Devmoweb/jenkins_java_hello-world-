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
        }

     stages{
        stage("BUILD .WAR FILE"){
            steps{
               bat 'mvn package'
                 }
             }
        }
   
}
