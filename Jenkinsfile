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
        stage("deploy on QA server for test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'h1', path: '', url: 'http://65.0.32.153:8080')], contextPath: '/app', war: '**/*.war'
                }
             }
        stage("Deploy on production server"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'h1', path: '', url: 'http://13.127.126.0:8080')], contextPath: '/app', war: '**/*.war'
                }
             }

        }

   
}
