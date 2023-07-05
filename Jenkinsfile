pipeline {
  agent any 
  // environment{
  //   DOCKER_TAG = getDockerTag{}
  // }
    stages {
        // stage("git Checkout"){
        //   steps{
        //       git branch: 'main', url: 'https://github.com/ayush11122/Pipeline.git'
        //   }
        // }
      stage("build docker image") {
        steps {
            sh "docker build -t ayush11122/pipeline . " 
        }
      }
      stage("Push to DockerHub") {
        steps {
          withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhubpwd')]) {
            sh """
                echo hello
                Docker login -u ayush11122 -p ${dockerhubpwd}
                echo hello2
                Docker push ayush11122/pipeline
                echo hello3
               """
            }
          }
      }
    }
}
  
  // def getDockerTag() {
  //   def tag = sh script: 'get rev-parse HEAD', returnStdout: true
  //   return tag
  // }
 