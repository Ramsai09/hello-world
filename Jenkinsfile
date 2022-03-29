
pipeline{
    agent any
    environment{
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("Git Checkout"){
            steps{
               git credentialsId: 'github', url: 'https://github.com/Ramsai09/hello-world.git'
            }
        }
        stage("maven build") {
            steps{
                sh "mvn clean package"
                
            }
        }
        stage("deploy") {
            steps {
                sshagent(['tomcat1']) {
                    sh"""
                      scp -o StrictHostKeyChecking=no targer/webapp.war ec2-user@172.31.83.109:/opt/tomcat/webapps/
                      ssh ec2-user@172.31.83.109 /opt/tomcat/bin/shutdown.sh
                      ssh ec2-user@172.31.83.109 /opt/tomcat/bin/startup.sh
                      
                    """
            }    
        }
    }
  }
}
