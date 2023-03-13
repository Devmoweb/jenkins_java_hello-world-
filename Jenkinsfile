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
        stage("test on QA server"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'h1', path: '', url: 'http://65.0.32.153:8080')], contextPath: '/app', war: '**/*.war'
                }
             }

        }

   
}
