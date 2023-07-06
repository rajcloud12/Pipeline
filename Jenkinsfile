pipeline {
    agent any 

    stages {
        stage('Static Code Analysis') {
             environment {
            SONAR_URL = "http://15.207.54.59:9000"
            }
            steps {
                // withSonarQubeEnv('SonarQube') {
              //  sh """
              // sonar-scanner \
              // -Dsonar.projectKey=pipeline \
              // -Dsonar.sources=Pipeline \
              // -Dsonar.language=web \
              // -Dsonar.sourceEncoding=UTF-8 \
              // -Dsonar.host.url='http://15.207.54.59:9000' \
              // -Dsonar.login=sonarQube
              // """
                def scannerHome = tool 'SonarQube';
                 withSonarQubeEnv() {
                 sh "${scannerHome}/bin/sonar-scanner"
                  }
                echo "aaaz"
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


 