@Library('jenkins-shared-library') _

pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    stages {
        stage('Build and Scan') {
            steps {
                script {
                    // Call the shared function for SonarQube analysis
                    sonarRunSonarQubeAnalysis(
                        sonarEnv: 'sn1',  // Specify the SonarQube environment (can be 'sn1', 'sn2', etc.)
                        projectDir: 'my-demo-app'  // Path to the project directory
                    )
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true  // Wait for SonarQube Quality Gate to pass
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
