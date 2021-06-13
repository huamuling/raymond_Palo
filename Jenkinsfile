pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    environment{
        PATH = "/opt/maven/bin:$PATH"
}
  stages {
      stage('Build Code using Maven') {
            steps{
                sh "mvn package"
            }
        }

 stage('QA/UAT') {
            steps {
           sh "echo For QA team to do their test steps........."          
            }
        }

        stage('Deploy on Tomcat server') {
            steps{
                sshagent(['deployer_user1']) {
                    sh "scp -o StrictHostKeyChecking=no target/webapp.war ec2-user@172.31.14.132:/opt/tomcat/webapps"
                }
            }
        }
            
    }
}
