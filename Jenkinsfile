
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
    }
}
