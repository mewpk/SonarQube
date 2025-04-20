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
                    // ทำการ clean และ build โปรเจกต์ก่อน
                    sh './gradlew clean build'
                    
                    // รัน SonarQube analysis หลังจากที่ build เสร็จ
                    sh './gradlew sonarqube --info'
                }
            }
        }
    }
}

}
