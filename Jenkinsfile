
pipeline{
    agent any
    stages {
        stage("Git Checkout"){
            steps{
               git credentialsId: 'github', url: 'https://github.com/Ramsai09/hello-world.git'
            }
        }
    }
}
