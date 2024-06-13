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
    stage('Build and push the docker image'){
      steps{
          script{
            args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
            sh 'docker build -t basic_image:1.0 .'
          }
      }
    }
  }
}
