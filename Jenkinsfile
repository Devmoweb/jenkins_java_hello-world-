pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage("Test on Local Machine") {
            steps {
                bat 'mvn test'
            }
        }
        stage("Build WAR File") {
            steps {
                bat 'mvn package'
            }
        }
        stage("Deploy to QA Server for Test") {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'h1', path: '', url: 'http://65.0.32.153:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage("Deploy to Production Server") {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'h1', path: '', url: 'http://13.127.126.0:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage("Send Notification Email") {
            steps {
                emailext body: "The build of the Maven project is completed successfully and deployed to QA and production servers.",
                         subject: "Jenkins Build Notification",
                         to: "devops.moweb@gmail.com",
                         mimeType: 'text/html'
            }
        }
        stage("Clean Up Old Builds") {
            steps {
                deleteDir()
            }
        }
    }
}
