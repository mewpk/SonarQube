pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build and Scan') {
      steps {
        dir('my-demo-app') {
          withSonarQubeEnv(installationName: 'sn1') {
            // Clean and build the project first
            sh './gradlew clean build'
            
            // Run SonarQube analysis after build
            sh './gradlew sonarqube --info'
          }
        }
      }
    }
    stage("Quality Gate") {
      steps {
        timeout(time: 5, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
  post {
    always {
      script {
        // Clean up the workspace after the build
        cleanWs()
      }
    }
    success {
      echo 'Build and SonarQube analysis completed successfully.'
    }
    failure {
      echo 'Build or SonarQube analysis failed.'
    }
  }
}
