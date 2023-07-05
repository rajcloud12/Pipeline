pipeline {
    agent any 

    stages {
        stage('Static Code Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    // Analyze the HTML/CSS files
                   echo "herlloo"
                }
            }
        }

      // stage("build docker image") {
      //   steps {
      //       sh "docker build -t ayush11122/pipeline ." 
      //   }
      // }
      // stage("Login and Push to DockerHub") {
      //   steps {
      //     withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhubpwd')]) {
      //       sh """
      //           docker login -u ayush11122 -p ${dockerhubpwd}
      //           docker push ayush11122/pipeline
      //          """
      //       }
      //     }
      // }
    }
}
 