pipeline {
  agent any
  tools {
        maven 'Maven 3.6.3' 
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
  }
}
