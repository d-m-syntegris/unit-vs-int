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
                    sh "${scannerHome}/bin/sonar-scanner \
                          -D sonar.login=cb5382d539272f1b950fe3cfa0547a73bc83723f \
                          -D sonar.projectKey=sonarqubetest \
                          -D sonar.exclusions=vendor/**,resources/**,**/*.java \
                          -D sonar.host.url=http://172.17.0.3:9000/"
                }
            }
        }

    }
}