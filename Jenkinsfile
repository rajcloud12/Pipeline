pipeline {
    agent any 

      stages {
        stage('SonarQube analysis') {
          environment {
            SCANNER_HOME = tool 'SonarQube'
          }
          steps {
            withSonarQubeEnv(credentialsId: 'sonarqube', installationName: 'SonarQube') {
              sh '''$SCANNER_HOME/bin/sonar-scanner \
              -Dsonar.projectKey=pipeline \
              -Dsonar.projectName=Pipeline \
              -Dsonar.sources=/var/lib/jenkins/workspace/Pipeline \
              -Dsonar.java.binaries=target/classes/ \
              -Dsonar.exclusions=src/test/java/****/*.java \
              -Dsonar.java.libraries=/var/lib/jenkins/.m2/**/*.jar \
              -Dsonar.projectVersion=${BUILD_NUMBER}-${GIT_COMMIT_SHORT}'''
            }
          }
        }
        stage("build docker image") {
          steps {
              sh "docker build -t rajcloud12/Pipeline ." 
          }
        }
        stage("Login and Push to DockerHub") {
          steps {
            withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhubpwd')]) {
              sh """
                  docker login -u rajcloud12 -p ${dockerhubpwd}
                  docker push rajcloud12/Pipeline
                """
              }
            }
        }
        stage("kubernetes deployment"){
          steps {
        
         sh "kubectl apply -f Deployment-service.yaml"
          }
        }
      }
}

 
