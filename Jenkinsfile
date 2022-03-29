
pipeline{
    agent any
    environment{
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("Git Checkout"){
            steps{
                //Pulling code from repo
               git credentialsId: 'github', url: 'https://github.com/Ramsai09/hello-world.git'
            }
        }
        stage("maven build") {
            steps{
                //maven build
                sh "mvn clean package"
            }
        }
        stage("deploy") {
            steps {   
                //deploy on tomcat
              sh "curl -v -u tomcat:s3cret -T /var/lib/jenkins/workspace/Jenkinsfile/webapp/target/webapp.war  'http://ec2-44-202-99-205.compute-1.amazonaws.com:8080//manager/text/deploy?path=/pipeline-maven'" 
        }
    }
        stage("success") {
            steps {
                script {
                    currentBuild.result = 'FAILURE'
                }
            }
        }  
               
  }
}
