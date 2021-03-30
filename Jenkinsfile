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
                          -D sonar.login=admin \
                          -D sonar.password=Ksk.1989 \
                          -D sonar.exclusions=vendor/**,resources/**,**/*.java \
                          -D sonar.host.url=http://172.17.0.3:9000/"
                }
            }
        }

    }
}