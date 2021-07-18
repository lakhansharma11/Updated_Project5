
pipeline {
    agent any
     tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
    stages {
        stage("clone code"){
            steps{
               git 'https://github.com/lakhansharma11/Updated_Project5.git'
            }
        }
        stage("build code"){
            steps{
              sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['deploy_user']) {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@13.229.183.126:/opt/apache-tomcat-8.5.55/webapps"
                 
                }
            }
        }
    }
}
