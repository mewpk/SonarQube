pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        dir('my-demo-app') {
          withSonarQubeEnv(installationName: 'sn1') { 
            sh './mvnw clean sonar:sonar'
          }
        }
      }
    }
  }
}
