pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build and SonarQube Analysis') {
        steps {
            script {
                // Build project
                sh './gradlew build'

                // Run SonarQube analysis
                sh './gradlew sonarqube'
            }
        }
    }
  }
}

