pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    environment{
        PATH = "/opt/maven/bin:$PATH"
}

      stage('Build Code using Maven') {
            steps{
                sh "mvn package"
            }
        }
        stage('Deploy on Tomcat server') {
            steps{
                sshagent(['deployer_user1']) {
                    sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.14.132:/opt/tomcat/webapps"
                }
            }
        }
            
    }
}
