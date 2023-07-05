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
    }
  }
  
  // def getDockerTag() {
  //   def tag = sh script: 'get rev-parse HEAD', returnStdout: true
  //   return tag
  // }
 