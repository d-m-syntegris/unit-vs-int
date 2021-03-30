pipeline {
    agent any

    stages {
        stage('Compile Stage') {
            steps {
                withMaven(maven : 'maven 3.6.3') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Test Stage') {
            steps {
                withMaven(maven : 'maven 3.6.3') {
                    sh 'mvn test'
                }
            }
        }

        stage('Sonarqube') {
            environment {
                scannerHome = tool 'SonarQubeScanner'
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "mvn sonar:sonar"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }

    }
}