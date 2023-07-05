pipeline {
    agent any 

    stages {
      
      stage("build docker image") {
        steps {
            sh "docker build -t ayush11122/pipeline ." 
        }
      }
      stage("Push to DockerHub") {
        steps {
          withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhubpwd')]) {
            sh """
                echo hello
                docker login -u ayush11122 -p ${dockerhubpwd}
                echo hello2
                docker push ayush11122/pipeline
                echo hello3
               """
            }
          }
      }
    }
}
 