pipeline {
  agent any
  tools {
        maven 'maven' 
    }
  stages {
    stage('Checkout') {
      steps {
        sh 'echo passed'
        git branch: 'main', url: 'https://github.com/ramakrishnachanchali/jenkinsCICD.git'
      }
    }
    stage('Build and Test') {
      steps {
        sh 'ls -ltr'
        // build the project and create a JAR file
        sh 'mvn clean package'
      }
    }
    stage('Sonar Scan'){
      environment{
        SONAR_URL = '192.168.29.66:9000/'
      }
      steps{
        withCredentials([string(credentialsId: 'sonar', variable: 'SONAR_AUTH_TOKEN')]) {
        sh 'cd mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
      }
    }
    stage('Build and push the docker image'){
      steps{
          script{
            sh 'whoami'
            sh 'docker build -t basic_image:1.0 .'
          }
      }
    }
  }
}
